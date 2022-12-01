## Yaroslav Abrasimov - Frontend Web Developer

### Personal information
- Date of birthday: **30/11/1994**
- Address: **Bratislava | Slovakia**
- Phone: **(063)-537-53-40**
- Email: **[yabrasimov94@gmail.com](mailto:yabrasimov94@gmail.com)**
- Git: **[https://github.com/Ferri0](https://github.com/Ferri0)**

### About me
I have been working as a front-end developer for about two years. Now I am actively studying backend and cloud technologies.  
I graduated from the RSSchool courses in 2019-2020.  
This year I came to RSSchool curse to keep my wife company, she is also studying to be a developer.

### Skills
| Skill                 | Rating                     |
|-----------------------|----------------------------|
| HTML5/CSS/SCSS        | ★ ★ ★ ★ ★                  |
| JavaScript            | ★ ★ ★ ★ ★                  |
| TypeScript            | ★ ★ ★ ☆ ☆                  |
| Git                   | ★ ★ ★ ★ ☆                  |
| React                 | ★ ★ ★ ★ ★                  |
| Redux                 | ★ ★ ★ ★ ☆                  |
| REST API              | ★ ★ ★ ★ ☆                  |
| GraphQL/Apollo Client | ★ ★ ★ ★ ☆                  |
| Webpack               | ★ ★ ★ ☆ ☆                  |
| Node.js               | ★ ★ ★ ☆ ☆                  |
| Next.js               | ★ ★ ★ ☆ ☆                  |


### Code example
```js
import fs from "fs/promises";
import path from "path";

import { isDirectory } from "./isDirectory.js";

/**
 * Service function, recursively copy all files from one folder to another
 * Able to handle nested folders
 *
 * @param {string} folderPath - Initial folder path (copy from)
 * @param {string} newFolderPath - Target folder path (copy to)
 * @returns {Promise<void>}
 */
export const copyFolderContent = async (folderPath, newFolderPath) => {
    const folderContent = await fs.readdir(folderPath)

    for (let i = 0; i < folderContent.length; i++) {
        const fileName = folderContent[i];

        const filePath = path.join(folderPath, fileName)

        if (await isDirectory(filePath)) {
            const innerFolderPath = path.join(folderPath, fileName);
            const newInnerFolderPath = path.join(newFolderPath, fileName);

            await fs.mkdir(newInnerFolderPath)
            await copyFolderContent(innerFolderPath, newInnerFolderPath)
        } else {
            await fs.copyFile(filePath, path.join(newFolderPath, fileName))
        }
    }
}
```
