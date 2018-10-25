---
title: JavaScript
description: Informations sur la prise en charge de JavaScript dans Visual Studio pour Mac
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 6efc22f916973f292daa97bdd6b5129ac9311f04
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881070"
---
# <a name="javascript-support"></a>Prise en charge de JavaScript

Visual Studio pour Mac prend en charge la mise en surbrillance de la syntaxe, la mise en forme du code et IntelliSense pour JavaScript et TypeScript. 

![Prise en charge de l’éditeur TypeScript](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

Pour plus d’informations, consultez les guides sur [l’écriture de code JavaScript](https://docs.microsoft.com/scripting/javascript/writing-javascript-code).

## <a name="adding-a-javascript-file"></a>Ajout d’un fichier JavaScript

Dans la plupart des cas, vous ajoutez des fichiers JavaScript à des projets ASP.NET Core à l’aide de la boîte de dialogue **Nouveau fichier**. Pour ajouter un fichier JavaScript, cliquez avec le bouton droit sur votre projet et accédez à **Ajouter > Nouveau fichier** : 

![Ajout de nouveaux fichiers au projet](media/javascript-image1.png)

Dans la boîte de dialogue Nouveau fichier, sélectionnez **Web > Fichier JS vide** ou **Web > Fichier TypeScript**. Nommez-le, puis choisissez **Nouveau** :

![Création d’un fichier TypeScript à partir du modèle](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio pour Mac utilise [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) pour fournir Intellisense. Vous disposez ainsi de la saisie semi-automatique du code, d’informations sur les paramètres et de listes de membres quand vous écrivez du code.

JavaScript Intellisense dans Visual Studio pour Mac peut reposer sur l’inférence de type, JSDoc ou la déclaration TypeScript.

- **Inférence de type** : le type d’un objet est déterminé par le contexte du code. Pour plus d’informations, consultez la section [IntelliSense basé sur l’inférence de type](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference) propre à Visual Studio.
- **JSDoc** : il peut arriver que l’inférence de type ne fournisse pas les bonnes informations de type. Dans ces cas, les informations de type peuvent être fournies explicitement par les annotations [JSDoc](http://usejsdoc.org/about-getting-started.html). Pour plus d’informations, consultez la section [IntelliSense basé sur JSDoc](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc) (Visual Studio).
- **Fichiers de déclaration typeScript** : les fichiers `.d.ts` sont utilisés pour fournir des valeurs à JavaScript Intellisense. Les types déclarés dans ce fichier peuvent être utilisés comme types dans les commentaires JSDoc. Pour plus d’informations, consultez la section [IntelliSense basé sur des fichiers de déclaration TypeScript](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) (Visual Studio). ![Ajout d’un fichier de définition TypeScript](media/javascript-image3.png)