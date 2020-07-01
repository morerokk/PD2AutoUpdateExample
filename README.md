# PAYDAY 2 auto-updating mod example
This is an example mod for PAYDAY 2 SuperBLT that does nothing by itself. Instead, it showcases the ability to use Github Actions to automatically build zip archives of your mods and have users automatically download these.

# Setup
Download or clone this repo. Copy the entire .github folder to your own project's root folder, and modify the sample meta.json and releases.yml as you see fit.
For the simplest configuration, simply change `SampleMod` in release.yml to point to your mod's root folder, and change `pd2autoupdatexample.zip` to a more personal zip name that will be used for your mod's zip files.
Don't forget to change the `ident` field in meta.json to your own mod's ID!

This template needs your mod's main folder to be *under* your repository's root. If your mod.txt file is inside the root of the repository, the hash checks won't function properly anymore, so move the mod into a child folder.

After you modify meta.json and releases.yml to match your own mod's ID and zip names, you are ready to commit and push. On your first push *or* your first pull request towards master, Github should immediately start performing all actions.
This action will delete any existing releases and make a new one, where it will upload your mod's zip file and meta.json. **Remember that the default behavior is to haphazardly delete any other releases or tags in the Releases section.**

Copy the direct download link for your mod's zip, and put it inside `.github/meta.json`. Copy the direct download link for your release's meta.json file, and put it in the updates section of your mod.txt file.

Commit and push these changes again, and your mod should be ready to go! Any pushes to master will immediately be zipped and made available to users ingame. Github will zip your mod for you and calculate a new hash.

# Dealing with line endings
Line endings may or may not (probably not) negatively affect the way the hashing works, which might endlessly pester your users with non-existent updates.
If this happens to you, copy the provided `.gitattributes` file into your own repository to prevent Git from messing with your line endings.

# Misc Info
The included SuperBLT hash calculator was made by fragtrane: https://github.com/fragtrane/Python-SuperBLT-Hash-Calculator
7-Zip by Igor Pavlov: https://www.7-zip.org/

7-zip is included and has to be used because SuperBLT's unzipper is incompatible with Powershell's `Compress-Archive` or the `tar` command.
