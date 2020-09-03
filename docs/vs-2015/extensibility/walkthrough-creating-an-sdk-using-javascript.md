---
title: 'Procédure pas à pas : création d’un SDK à l’aide de JavaScript | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e953d9051b9bc7e95dc29e02eb580c4d93fca26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148833"
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>Procédure pas à pas : création d’un SDK en JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas explique comment utiliser JavaScript pour créer un kit de développement logiciel (SDK) Math simple en tant qu’extension Visual Studio (VSIX).  La procédure pas à pas est divisée en plusieurs parties :  
  
- [Pour créer le projet SDK d’extension SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
- [Pour créer un exemple d’application qui utilise le kit de développement logiciel (SDK)](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
  Pour JavaScript, il n’existe aucun type de projet de bibliothèque de classes. Dans cette procédure pas à pas, l’exemple de fichier arithmetic.js est créé directement dans le projet VSIX. Dans la pratique, nous vous recommandons d’abord de créer et de tester les fichiers JavaScript et CSS en tant qu’application du Windows Store, par exemple à l’aide du modèle d' **application vide** , avant de les placer dans un projet VSIX.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a> Pour créer le projet SDK d’extension SimpleMathVSIX  
  
1. Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2. Dans la liste des catégories de modèles, sous **Visual C#**, sélectionnez **extensibilité**, puis sélectionnez le modèle de **projet VSIX** .  
  
3. Dans la zone de texte **nom** , spécifiez `SimpleMathVSIX` et choisissez le bouton **OK** .  
  
4. Si l **'Assistant package Visual Studio** s’affiche, cliquez sur le bouton **suivant** dans la page d' **Accueil** , puis sur la **page 1 de 7**, choisissez le bouton **Terminer** .  
  
     Bien que le **Concepteur de manifeste** s’ouvre, nous allons simplifier cette procédure pas à pas en modifiant directement le fichier manifeste.  
  
5. Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier source. extension. vsixmanifest, puis choisissez **afficher le code**. Utilisez ce code pour remplacer le contenu existant dans le fichier.  
  
    ```  
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
  
6. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet SimpleMathVSIX, puis choisissez **Ajouter**, **nouvel élément**.  
  
7. Dans la catégorie **données** , sélectionnez **fichier XML**, nommez le fichier `SDKManifest.xml` , puis cliquez sur le bouton **Ajouter** .  
  
8. Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier SDKManifest.xml, puis choisissez **ouvrir** pour afficher le fichier dans l' **éditeur XML**.  
  
9. Ajoutez le code suivant au fichier SDKManifest.xml.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. Dans **Explorateur de solutions**, dans le menu contextuel du fichier SDKManifest.xml, choisissez **Propriétés**.  
  
11. Dans la fenêtre **Propriétés** , affectez à la propriété **inclure dans VSIX** la **valeur true**.  
  
12. Dans **Explorateur de solutions**, dans le menu contextuel du projet SimpleMathVSIX, choisissez **Ajouter**, **nouveau dossier**, puis nommez le dossier `Redist` .  
  
13. Ajoutez des sous-dossiers sous Redist pour créer cette structure de dossiers :  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. Dans le menu contextuel du dossier \js\, choisissez **Ajouter**, **nouvel élément**.  
  
15. Sous **éléments Visual C#**, sélectionnez la catégorie **Web** , puis sélectionnez l’élément de **fichier JavaScript** . Nommez le fichier `arithmetic.js` , puis cliquez sur le bouton **Ajouter** .  
  
16. Insérez le code suivant dans arithmetic.js :  
  
    ```  
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
  
17. Dans **Explorateur de solutions**, dans le menu contextuel du fichier arithmetic.js, choisissez **Propriétés**. Modifiez les propriétés suivantes :  
  
    - Affectez à la propriété **inclure dans VSIX** la **valeur true**.  
  
    - Définissez la propriété **copier dans le répertoire de sortie** sur **toujours copier**.  
  
18. Dans **Explorateur de solutions**, dans le menu contextuel du projet SimpleMathVSIX, choisissez **générer**.  
  
19. Une fois la génération terminée, dans le menu contextuel du projet, choisissez **ouvrir le dossier dans l’Explorateur de fichiers**. Accédez à \bin\debug \\ , puis exécutez `SimpleMathVSIX.vsix` pour l’installer.  
  
20. Choisissez le bouton **installer** et laissez l’installation terminée.  
  
21. Démarrez Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a> Pour créer un exemple d’application qui utilise le kit de développement logiciel (SDK)  
  
1. Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2. Dans la liste des catégories de modèles, sous **JavaScript**, sélectionnez **Windows Store**, puis sélectionnez le modèle **application vide** .  
  
3. Dans la zone **nom** , spécifiez `ArithmeticUI` . Choisissez le bouton **OK**.  
  
4. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet ArithmeticUI, puis choisissez **Ajouter**, **référence**.  
  
5. Sous **Windows**, choisissez **Extensions**, et notez que la **simple mathématique** est affichée.  
  
6. Activez la case à cocher **Math simple** , puis cliquez sur le bouton **OK** .  
  
7. Dans **Explorateur de solutions**, sous **références**, Notez que la référence **mathématique simple** est affichée. Développez-le et Notez qu’il existe un dossier \js\ qui inclut arithmetic.js. Vous pouvez ouvrir arithmetic.js pour vérifier que le code source a été installé.  
  
8. Utilisez le code suivant pour remplacer le contenu de default.htm.  
  
    ```  
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
  
9. Utilisez le code suivant pour remplacer le contenu de \js\default.js.  
  
    ```  
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
  
10. Remplacez le contenu de \css\default.css par ce code :  
  
    ```  
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
  
11. Appuyez sur la touche F5 pour générer et exécuter l’application.  
  
12. Dans l’interface utilisateur de l’application, entrez deux nombres, sélectionnez une opération, puis cliquez sur le **=** bouton. Le résultat correct s’affiche.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un Kit de développement logiciel (SDK)](../extensibility/creating-a-software-development-kit.md)
