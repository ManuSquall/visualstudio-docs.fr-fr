---
title: Prise en main avec le modèle de projet VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc3f461c9e7dbdea1fd8481594292a0a247d2173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204296"
---
# <a name="getting-started-with-the-vsix-project-template"></a>Bien démarrer avec le modèle de projet VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser le modèle de projet VSIX pour créer une extension ou pour empaqueter une extension existante en vue d’un déploiement. Le modèle de projet VSIX a à la fois des versions Visual Basic et Visual C#, et est installé dans le cadre du kit de développement logiciel (SDK) Visual Studio.  
  
 Le modèle de projet VSIX se compose juste d’un fichier. extension. vsixmanifest source, qui contient des informations sur l’extension et les ressources qu’elle envoie.  
  
 Pour rechercher le modèle de projet VSIX, vous devez installer le kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Déploiement d’un modèle de projet personnalisé à l’aide du modèle de projet VSIX  
 Les étapes suivantes montrent comment utiliser le projet VSIX pour empaqueter un modèle de projet que vous pouvez partager avec d’autres développeurs ou télécharger dans la Galerie Visual Studio.  
  
1. Créez un modèle de projet.  
  
    1. Ouvrez le projet à partir duquel créer un modèle. Ce projet peut être de n’importe quel type de projet.  
  
    2. Dans le menu **Fichier**, cliquez sur **Exporter le modèle**. Effectuez les étapes de l’Assistant.  
  
         Un fichier. zip est créé dans%USERPROFILE%\My Documents\Visual Studio \Mes Exported *\<version>* Templates \\ .  
  
2. Créez un projet VSIX vide.  
  
     Dans le menu **Fichier**, cliquez sur **Nouveau**, puis cliquez sur **Projet**. Sélectionnez **Visual Basic** ou **Visual C#**. Sous le nœud sélectionné, sélectionnez **extensibilité**, puis **projet VSIX**.  
  
3. Ajoutez le fichier. zip au projet. Affectez à la propriété **copier dans le répertoire de sortie** la valeur `Copy Always` .  
  
4. Dans le **Explorateur de solutions**, double-cliquez sur le `source.extension.vsixmanifest` fichier pour l’ouvrir dans le **Concepteur de manifeste VSIX**, puis apportez les modifications suivantes :  
  
    - Définissez le champ **nom du produit** sur **mon modèle de projet**.  
  
    - Définissez le champ **Product ID** sur **MyProjectTemplate-1**.  
  
    - Définissez le champ **auteur** sur **Fabrikam**.  
  
    - Définissez le champ **Description** sur **mon modèle de projet**.  
  
    - Dans la section **ressources** , ajoutez un type **Microsoft. VisualStudio. ProjectTemplate** et définissez son chemin d’accès sur le nom du fichier. zip.  
  
5. Enregistrez et fermez le fichier source. extension. vsixmanifest.  
  
6. Créez le projet.  
  
7. Dans le répertoire de sortie, double-cliquez sur le fichier. vsix.  
  
8. Une boîte de message du **programme d’installation VSIX** s’affiche. Suivez les instructions pour installer l’extension.  
  
9. Fermez Visual Studio, puis rouvrez-le.  
  
10. Sélectionnez **extensions et mises à jour** (dans le menu **Outils** ) et sélectionnez la catégorie **modèles** . L’une des extensions disponibles doit être **mon modèle de projet**.  
  
11. Le nouveau modèle de projet s’affiche dans la boîte de dialogue **nouveau projet** au même emplacement que le modèle de projet d’origine. Par exemple, si vous avez créé un modèle nommé **console VB** à partir d’une application console Visual Basic, la **console VB** apparaît dans le même volet que le modèle **application console** Visual Basic.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Pour spécifier l’emplacement du modèle dans la boîte de dialogue Nouveau projet  
  
1. Les dossiers de modèles se trouvent dans le *chemin d’installation de Visual Studio*\Common7\IDE\ProjectTemplates et dans les répertoires \Common7\IDE\ItemTemplates du *chemin d’installation de Visual Studio*. Les noms des sections de niveau supérieur dans la boîte de dialogue Nouveau projet ne correspondent pas exactement aux noms des dossiers de modèles. À l’endroit où ils diffèrent, utilisez le nom du dossier de modèles.  
  
     Remplacez l’extension de fichier. vsix par. zip, puis ouvrez le fichier.  
  
2. Créez un nouveau dossier portant le même nom que la section de la boîte de dialogue Nouveau projet. le modèle doit apparaître dans.  
  
3. Si le modèle doit apparaître dans une sous-section, créez un sous-dossier du même nom.  
  
4. Déplacez le fichier Template. zip dans le nouveau dossier.  
  
5. Remplacez l’extension. zip par. vsix.  
  
6. Ouvrez le manifeste VSIX.  
  
7. Dans le manifeste VSIX, mettez à jour le chemin d’accès de l' **élément** multimédia du modèle afin qu’il pointe vers la racine de l’arborescence de répertoires qui contient le fichier de modèle. Par exemple, si le modèle se trouve dans \CSharp\Windows, la référence doit pointer vers \CSharp.
