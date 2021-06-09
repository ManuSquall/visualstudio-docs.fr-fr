---
title: JavaScript et TypeScript
description: Informations sur la prise en charge de JavaScript dans Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 5f1a400506f7766ba22ffbc1debde687b1709a21
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760924"
---
# <a name="javascript-and-typescript-support"></a>Prise en charge de JavaScript et TypeScript

Visual Studio pour Mac assure une prise en charge de JavaScript et TypeScript à travers la mise en surbrillance de la syntaxe, la mise en forme du code et IntelliSense.

![Prise en charge de l’éditeur TypeScript](/visualstudio/mac/media/tsjseditor-2019.gif)

Pour plus d’informations sur l’écriture JavaScript, consultez les guides sur l’[écriture de code JavaScript](/scripting/javascript/writing-javascript-code).

## <a name="adding-a-javascript-file"></a>Ajout d’un fichier JavaScript

Dans la plupart des cas, vous ajoutez des fichiers JavaScript à des projets ASP.NET Core à l’aide de la boîte de dialogue **Nouveau fichier**. Pour ajouter un fichier JavaScript, cliquez avec le bouton droit sur votre projet et accédez à **Ajouter > Nouveau fichier** :

![Ajout de nouveaux fichiers au projet](media/javascript-image1.png)

Dans la boîte de dialogue **Nouveau fichier**, sélectionnez **Web > Fichier JS vide** ou **Web > Fichier TypeScript**. Nommez-le, puis choisissez **Nouveau** :

![Création d’un fichier TypeScript à partir du modèle](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio pour Mac utilise [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) pour fournir IntelliSense. Vous disposez ainsi de la saisie semi-automatique du code, d’informations sur les paramètres et de listes de membres quand vous écrivez du code.

JavaScript IntelliSense dans Visual Studio pour Mac peut être basé sur l’inférence de type, JSDoc ou la déclaration TypeScript.

- **Inférence de type** : le type d’un objet est déterminé par le contexte du code. Pour plus d’informations, consultez la section [IntelliSense basé sur l’inférence de type](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference) propre à Visual Studio.
- **JSDoc** : il peut arriver que l’inférence de type ne fournisse pas les bonnes informations de type. Dans ces cas, les informations de type peuvent être fournies explicitement par les annotations [JSDoc](https://jsdoc.app/about-getting-started.html). Pour plus d’informations, consultez la section [IntelliSense basé sur JSDoc](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc) (Visual Studio).
- **Fichiers de déclaration de machine à écrire** : `.d.ts` les fichiers sont utilisés pour fournir des valeurs pour JavaScript IntelliSense. Les types déclarés dans ce fichier peuvent être utilisés comme types dans les commentaires JSDoc. Pour plus d’informations, consultez la section [IntelliSense basé sur les fichiers de déclaration TypeScript](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) dans la documentation de Visual Studio.

    ![ajout d’un fichier de définition TypeScript](media/javascript-image3.png)

## <a name="see-also"></a>Voir aussi

- [JavaScript IntelliSense (Visual Studio sur Windows)](/visualstudio/ide/javascript-intellisense)
