<%*
const baseFolder = "Lab Notes";
const templateFolder = `${baseFolder}/Templates`;
const year = moment().format("YYYY");
const month = moment().format("MM");
const monthName = moment().format("MMMM");
const weekNum = moment().format("[Week-]WW");

const config = {
  daily: {
    folder: `${baseFolder}/${year}/${month}`,
    filename: moment().format("YYYY-MM-DD"),
    template: `${templateFolder}/Daily Template`,
    condition: () => true // every day
  },
  weekly: {
    folder: `${baseFolder}/${year}/${month}`,
    filename: `${weekNum}-Review`,
    template: `${templateFolder}/Weekly Template`,
    condition: () => moment().day() === 1 // Monday
  },
  monthly: {
    folder: `${baseFolder}/${year}/${month}`,
    filename: `${monthName}-${year.slice(2)}-Review`,
    template: `${templateFolder}/Monthly Template`,
    condition: () => moment().date() === 1 // first of month
  },
  yearly: {
    folder: `${baseFolder}/${year}`,
    filename: `${year}-Review`,
    template: `${templateFolder}/Yearly Template`,
    condition: () => moment().dayOfYear() === 1 // Jan 1
  }
};

async function ensureFolder(path) {
  if (!app.vault.getAbstractFileByPath(path)) {
    await app.vault.createFolder(path);
  }
}

async function ensureNote(period) {
  const cfg = config[period];
  if (!cfg.condition()) return;

  const folderPath = cfg.folder;
  await ensureFolder(folderPath);

  const filepath = `${folderPath}/${cfg.filename}`;
  const fullPath = `${filepath}.md`;
  if (!app.vault.getAbstractFileByPath(fullPath)) {
  //  const template = await tp.file.find_tfile(cfg.template);
  //  await tp.file.create_new(template, "/" + filepath);
    const templateFile = await tp.file.find_tfile(cfg.template);
    const templateContent = await app.vault.read(templateFile);
    await app.vault.create(fullPath, templateContent);
    new Notice(`Created ${period} note: ${fullPath}`);
    await app.workspace.openLinkText(filepath, "", true);
  }
}

for (const p of Object.keys(config)) {
  await ensureNote(p);
}
%>
