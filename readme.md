# MODPACKNAME

DESCRIPTION

## File Structure

```
├─ mods/             For each mod in the modpack, a .pw.toml file will be created here
│  └─ .gitkeep       Just makes sure the ./mods/ folder is created for this example repo
├─ .packwizignore    Excludes files from packwiz's tracking
├─ index.toml        Manifest file that tracks installed mods
├─ LICENSE           Legalese
├─ MODPACKNAME.zip   A MultiMC modpack used during local development for playtesting
├─ pack.toml         Main packwiz file; contains Minecraft version and modloader version
└─ readme.md         The file you're reading right now
```

## Local Development

### Setup

- Install [`packwiz`](https://packwiz.infra.link/)
- Make sure you have an appropriate version of Java installed
- `git clone` this repo
- Using a MultiMC fork, create a new Minecraft instance. Choose to import from a zip file, then select `MODPACKNAME.zip` which is included in this repo.

### Commands

In your preferred terminal, `cd` into the cloned directory, then you can run the following commands:

```sh
packwiz curseforge add <mod> # add mod from curseforge.com/minecraft/mc-mods/<mod>
packwiz remove <mod>
packwiz update <mod>
packwiz update --all

packwiz serve # serve files on a local HTTP server, for playtesting via MultiMC
packwiz refresh # update index.toml to account for local files like configs, scripts, and datapacks
packwiz curseforge export # generate curseforge modpack
```

### Workflows

#### Playtesting

1. (Optional) Make changes:
   - Add, update, or remove mods via the above commands.
   - Add, edit, or remove config files, datapack files, KubeJS script files, etc.
2. When you're ready to playtest, run `packwiz serve`.
3. Launch your MODPACKNAME MultiMC instance. Every time you launch it, it fetches all the appropriate mod `.jar` files from CurseForge.
   - This means it will overwrite many files when you launch it again. You can (and should!) edit configs, datapacks, and scripts while the game is running, but take care to copy the changes you want to keep back to the repo folder before you launch again, lest you accidentally delete your work.

#### Git Flow: Committing

1. Run `packwiz refresh` to make `packwiz` aware of added and changed configs, scripts, datapacks, etc.
2. Commit your changes alongside the refreshed `index.toml`.

#### Editing the MODPACKNAME.zip File

1. Add the instance to your MultiMC fork via the "Import from zip" option.
2. Edit instance -> Settings, then make your edits.
3. Open the instance folder. There will be a `readme.md` in there explaining how to export the updated modpack zip file.
