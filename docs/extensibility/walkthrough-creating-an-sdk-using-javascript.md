---
title: 'Procédure pas à pas : Création d’un kit de développement à l’aide de JavaScript | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed81ac8e79db6a11dd4897b2d9f96c7c63d10294
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934993"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Procédure pas à pas : Créer un kit de développement à l’aide de JavaScript
Cette procédure pas à pas explique comment utiliser JavaScript pour créer un simple mathématiques SDK comme une Extension Visual Studio (VSIX).  La procédure pas à pas est divisée en différentes parties :  
  
- [Pour créer le projet SDK d’extension SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
- [Pour créer un exemple d’application qui utilise le Kit de développement](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
  Pour JavaScript, il n’existe aucun type de projet de bibliothèque de classe. Dans cette procédure pas à pas, l’exemple *arithmetic.js* fichier est créé directement dans le projet VSIX. Dans la pratique, nous vous recommandons d’abord générer et tester les fichiers JavaScript et CSS comme une application Windows Store, par exemple, en utilisant le **application vide** modèle — avant de les insérer dans un projet VSIX.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createSimpleMathVSIX"></a> Pour créer le projet SDK d’extension SimpleMathVSIX  
  
1.  Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.  
  
2.  Dans la liste des catégories de modèles, sous **Visual C#**, sélectionnez **extensibilité**, puis sélectionnez le **projet VSIX** modèle.  
  
3.  Dans le **nom** texte, spécifiez `SimpleMathVSIX` et choisissez le **OK** bouton.  
  
4.  Si le **Assistant Package Visual Studio** s’affiche, choisissez le **suivant** bouton sur le **Bienvenue** page, puis, dans **Page 1 de 7**, choisissez le **Terminer** bouton.  
  
     Bien que le **Concepteur de manifeste** s’ouvre, nous allons conserver cette procédure pas à pas simple en modifiant le fichier manifeste directement.  
  
5.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **source.extension.vsixmanifest** de fichiers, puis choisissez **afficher le Code**. Utilisez ce code pour remplacer le contenu existant dans le fichier.  
  
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
  
6.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SimpleMathVSIX** de projet, puis choisissez **ajouter** > **unnouvelélément**.  
  
7.  Dans le **données** catégorie, sélectionnez **fichier XML**, nommez le fichier `SDKManifest.xml`, puis choisissez le **ajouter** bouton.  
  
8.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SDKManifest.xml** de fichiers, puis choisissez **ouvrir** pour afficher le fichier dans le **éditeur XML**.  
  
9. Ajoutez le code suivant à la **SDKManifest.xml** fichier.  
  
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
  
10. Dans **l’Explorateur de solutions**, dans le menu contextuel pour le **SDKManifest.xml** de fichiers, choisissez **propriétés**.  
  
11. Dans le **propriétés** fenêtre, définissez la **inclure dans VSIX** propriété **True**.  
  
12. Dans **l’Explorateur de solutions**, dans le menu contextuel pour le **SimpleMathVSIX** de projet, choisissez **ajouter** > **nouveau dossier**, et Ensuite, nommez le dossier `Redist`.  
  
13. Ajouter des sous-dossiers sous Redist pour créer cette structure de dossiers :  
  
     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*  
  
14. Dans le menu contextuel pour le **\js\\**  dossier, choisissez **ajouter** > **un nouvel élément**.  
  
15. Sous **éléments Visual c#**, sélectionnez le **Web** catégorie, puis sélectionnez le **fichier JavaScript** élément. Nommez le fichier `arithmetic.js`, puis choisissez le **ajouter** bouton.  
  
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
  
17. Dans **l’Explorateur de solutions**, dans le menu contextuel pour le **arithmetic.js** de fichiers, choisissez **propriétés**. Effectuer ces modifications de propriété :  
  
    -   Définir le **inclure dans VSIX** propriété **True**.  
  
    -   Définir le **Copy to Output Directory** propriété **toujours copier**.  
  
18. Dans **l’Explorateur de solutions**, dans le menu contextuel pour le **SimpleMathVSIX** de projet, choisissez **Build**.  
  
19. Une fois la build terminée, dans le menu contextuel du projet, choisissez **ouvrir le dossier dans l’Explorateur de fichiers**. Accédez à **\bin\debug\\**et exécutez `SimpleMathVSIX.vsix` pour l’installer.  
  
20. Choisissez le **installer** bouton et laissez l’installation terminée.  
  
21. Redémarrez Visual Studio.  
  
##  <a name="createSampleApp"></a> Pour créer un exemple d’application qui utilise le Kit de développement  
  
1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.  
  
2. Dans la liste des catégories de modèles, sous **JavaScript**, sélectionnez **Windows Store**, puis sélectionnez le **application vide** modèle.  
  
3. Dans le **nom** , spécifiez `ArithmeticUI`. Sélectionnez le bouton **OK** .  
  
4. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ArithmeticUI** de projet, puis choisissez **ajouter** > **référence**.  
  
5. Sous **Windows**, choisissez **Extensions**et notez que **mathématiques simples** s’affiche.  
  
6. Sélectionnez le **mathématiques simples** case à cocher, puis choisissez le **OK** bouton.  
  
7. Dans **l’Explorateur de solutions**, sous **références**, notez que le **mathématiques simples** référence s’affiche. Développer et notez qu’il existe un **\js\\**  dossier inclut **arithmetic.js**. Vous pouvez ouvrir **arithmetic.js** pour confirmer que votre code source a été installé.  
  
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
  
9. Utilisez le code suivant pour remplacer le contenu de *\js\default.js*.  
  
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
  
10. Remplacez le contenu de *\css\default.css* avec ce code :  
  
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
  
11. Choisissez le **F5** clé pour générer et exécuter l’application.  
  
12. Dans l’interface utilisateur d’application, entrez tous les deux nombres, sélectionnez une opération, puis choisissez le **=** bouton. Le résultat correct apparaît.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un Kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)
