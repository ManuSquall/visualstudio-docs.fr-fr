---
title: 'Procédure pas à pas : Création d’un SDK à l’aide de JavaScript (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3a3fa110bd6521443521449898474299dd267d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697499"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Procédure pas à pas : Créez un SDK à l’aide de JavaScript
Ce pas-là enseigne comment utiliser JavaScript pour créer un simple SDK mathématiques comme une extension de studio visuel (VSIX).  La procédure pas à pas est divisée en ces parties :

- [Créer le projet d’extension SDK SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Pour créer une application d’échantillon qui utilise le SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  Pour JavaScript, il n’existe pas de type de projet de bibliothèque de classe. Dans cette procédure pas à pas, le fichier *arithmetic.js* de l’échantillon est créé directement dans le projet VSIX. Dans la pratique, nous vous recommandons d’abord de construire et de tester les fichiers JavaScript et CSS comme une application Windows Store, par exemple, en utilisant le modèle **Blank App,** avant de les mettre dans un projet VSIX.

## <a name="prerequisites"></a>Prérequis
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, voir [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>Créer le projet d’extension SDK SimpleMathVSIX

1. Sur la barre de menu, choisissez **File** > **New** > **Project**.

2. Dans la liste des catégories de modèles, sous **Visual C ,** sélectionnez **Extensibility,** puis sélectionnez le modèle **de projet VSIX.**

3. Dans la boîte à `SimpleMathVSIX` texte **Nom,** spécifiez et choisissez le bouton **OK.**

4. Si le **Visual Studio Package Wizard** apparaît, choisissez le bouton **Suivant** sur la page **Bienvenue,** puis sur **la page 1 de 7**, choisissez le bouton **Finition.**

     Bien que le **Concepteur Manifeste** s’ouvre, nous allons garder cette procédure pas à pas simple en modifiant le fichier manifeste directement.

5. Dans **Solution Explorer**, ouvrez le menu raccourci pour le fichier **source.extension.vsixmanifest,** puis choisissez View **Code**. Utilisez ce code pour remplacer le contenu existant dans le fichier.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />
        <DisplayName>Simple Math</DisplayName>
        <Description>Does basic arithmetic calculations.</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

6. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet **SimpleMathVSIX,** puis choisissez **Ajouter** > **un nouvel article**.

7. Dans la catégorie **Données,** sélectionnez le `SDKManifest.xml`fichier **XML**, nommez le fichier et choisissez le bouton **Ajouter.**

8. Dans **Solution Explorer**, ouvrez le menu raccourci pour le fichier **SDKManifest.xml,** puis choisissez **Open** pour afficher le fichier dans **l’éditeur XML**.

9. Ajoutez le code suivant au fichier **SDKManifest.xml.**

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. Dans **Solution Explorer**, sur le menu raccourci pour le fichier **SDKManifest.xml,** choisissez **Properties**.

11. Dans la fenêtre **propriété,** définissez la propriété Inclure dans LA propriété **VSIX** à **True**.

12. Dans **Solution Explorer**, sur le menu raccourci pour le projet **SimpleMathVSIX,** choisissez **Add** > **New Folder**, puis nommez le dossier `Redist`.

13. Ajoutez des sous-plis sous Redist pour créer cette structure de dossier :

     *"Redist-CommonConfiguration"Neutral’SimpleMath’js\\*

14. Sur le menu raccourci pour le dossier **\\ 'js',** choisissez **Ajouter** > **un nouvel article**.

15. Sous **les éléments Visual C,** sélectionnez la catégorie **Web,** puis sélectionnez l’élément **de fichier JavaScript.** Nommez `arithmetic.js`le fichier, puis choisissez le bouton **Ajouter.**

16. Insérez le code suivant dans *arithmetic.js*:

    ```csharp
    (function (global) {
        "use strict";
        global.Arithmetic = {
            add: function (firstNumber, secondNumber) {
                return firstNumber + secondNumber;
            },

            subtract: function (firstNumber, secondNumber) {
                return firstNumber - secondNumber;
            },

            multiply: function (firstNumber, secondNumber) {
                return firstNumber * secondNumber;
            },

            divide: function (firstNumber, secondNumber) {
                return firstNumber / secondNumber;
            }
        };
    })(this);

    ```

17. Dans **Solution Explorer**, sur le menu raccourci pour le fichier **arithmetic.js,** choisissez **Properties**. Effectuer ces changements de propriété:

    - Définissez la **propriété Inclure dans VSIX** à **True**.

    - Définissez la copie à la propriété **de l’annuaire de sortie** pour copier **toujours.**

18. Dans **Solution Explorer**, sur le menu raccourci pour le projet **SimpleMathVSIX,** choisissez **Build**.

19. Une fois la construction terminée avec succès, sur le menu raccourci pour le projet, choisissez **Open Folder dans File Explorer**. Naviguez **jusqu’à 'bin’debug,\\**et exécutez-le `SimpleMathVSIX.vsix` pour l’installer.

20. Choisissez le bouton **Installer** et laissez l’installation terminée.

21. Redémarrez Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>Pour créer une application d’échantillon qui utilise le SDK

1. Sur la barre de menu, choisissez **File** > **New** > **Project**.

2. Dans la liste des catégories de modèles, sous **JavaScript**, sélectionnez **Windows Store,** puis sélectionnez le modèle **Blank App.**

3. Dans la boîte `ArithmeticUI` **nomin,** spécifiez . Choisissez le bouton **OK**.

4. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet **ArithmeticUI,** puis choisissez **Add** > **Reference**.

5. Sous **Windows**, choisissez **Extensions**, et remarquez que **Simple Math** est affiché.

6. Sélectionnez la case à cocher **Simple Math,** puis choisissez le bouton **OK.**

7. Dans **Solution Explorer**, sous **Références**, remarquez que la référence Simple **Math** est affichée. Élargissez-le et remarquez qu’il ya un dossier **\\ js** qui comprend **arithmetic.js**. Vous pouvez ouvrir **arithmetic.js** pour confirmer que votre code source a été installé.

8. Utilisez le code suivant pour remplacer le contenu de *default.htm*.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8" />
       <title>ArithmeticUI</title>

       <!-- WinJS references -->
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>

       <!-- ArithmeticUI references -->
       <link href="/css/default.css" rel="stylesheet" />
       <script src="/js/default.js"></script>
       <script src="/SimpleMath/js/arithmetic.js"></script>
   </head>
   <body>
       <form>
       <div id="calculator" class="ms-grid">
           <input name="firstNumber" id="firstNumber" type="number" step="any">
           <div id="operators">
               <button class="operator" type="button">+</button>
               <button class="operator" type="button">-</button>
               <button class="operator" type="button">*</button>
               <button class="operator" type="button">/</button>
           </div>
           <input id="secondNumber" type="number">
           <button class="calculate" type="button">=</button>
           <input id="result" type="number" name="result" disabled="" readonly="">
       </div>
       </form>
   </body>
   </html>
   ```

9. Utilisez le code suivant pour remplacer le contenu de *'js’default.js*.

    ```csharp
    (function () {
        "use strict";

        var app = WinJS.Application;
        var operation = null;

        function calculateResult() {
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),
                result = 0;

            if (isNaN(firstNumber) || isNaN(secondNumber)) {
                result = 0;
            }
            else {
                switch (operation) {
                    case "+":
                        result = Arithmetic.add(firstNumber, secondNumber);
                        break;
                    case "-":
                        result = Arithmetic.subtract(firstNumber, secondNumber);
                        break;
                    case "*":
                        result = Arithmetic.multiply(firstNumber, secondNumber);
                        break;
                    case "/":
                        result = Arithmetic.divide(firstNumber, secondNumber);
                        break;
                    default:
                }
            }
            document.querySelector("#result").value = result.toString();
        }

        app.onactivated = function (args) {
            document.querySelector("#calculator").addEventListener("click", function (event) {
                if (event.target.tagName.toLowerCase() === "button") {
                    switch (event.target.className) {
                        case "operator":
                            operation = event.target.innerText;
                            break;
                        case "calculate":
                            calculateResult();
                            break;
                        default:
                            break;
                    }
                }
            });
        };

        app.start();
    })();
    ```

10. Remplacez le contenu de *l’adresse suivante :*

    ```xml
    form {
        display: -ms-grid;
        -ms-grid-rows: 1fr auto 1fr;
        -ms-grid-columns: 1fr auto 1fr;
        height: 100%;
        width: 100%;
    }

    button, input[type=number] {
        margin-right: 5px;
        -ms-grid-row-align: center;
    }

    #calculator {
        -ms-grid-column: 2;
        -ms-grid-row: 2;
        display: -ms-grid;
        -ms-grid-rows: 1fr;
        -ms-grid-columns: auto min-content auto auto auto;
    }

    .ms-grid input {
        width: 5em;
    }

    #firstNumber {
        -ms-grid-column: 1;
        -ms-grid-row-align: center;
    }

    #operators {
        -ms-grid-column: 2;
        -ms-grid-row-align: center;
    }

        #operators button.operator {
            margin-bottom: 5px;
            height: 40px;
        }

    #secondNumber {
        -ms-grid-column: 3;
    }

    button.calculate {
        -ms-grid-column: 4;
        -ms-grid-row-align: center;
        height: 40px;
    }

    #result {
        -ms-grid-column: 5;
    }

    ```

11. Choisissez la clé **F5** pour construire et exécuter l’application.

12. Dans l’interface utilisateur de l’application, entrez deux **=** numéros, sélectionnez une opération, puis choisissez le bouton. Le résultat correct apparaît.

## <a name="see-also"></a>Voir aussi
- [Créer un Kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)
