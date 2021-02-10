---
title: Personnaliser le package de solution SharePoint à l’aide de cibles MSBuild
titleSuffix: ''
description: Personnaliser la façon dont Visual Studio crée les fichiers de package de solution SharePoint (. wsp) à l’aide des cibles MSBuild à partir d’une invite de commandes.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b4d181a6310e1ff924f060e906093d3c28d60ede
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959920"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Comment : personnaliser un package de solution SharePoint à l’aide de cibles MSBuild
  En utilisant des cibles MSBuild dans une invite de commandes, vous pouvez personnaliser la façon dont Visual Studio crée les fichiers de package SharePoint (*. wsp*). Par exemple, vous pouvez personnaliser les propriétés MSBuild pour modifier le répertoire intermédiaire de Packaging et les groupes d’éléments MSBuild qui spécifient les fichiers énumérés.

## <a name="customize-and-run-msbuild-targets"></a>Personnaliser et exécuter des cibles MSBuild
 Si vous personnalisez les cibles BeforeLayout et AfterLayout, vous pouvez effectuer des tâches avant la mise en page du package, telles que l’ajout, la suppression ou la modification de fichiers qui seront empaquetés.

#### <a name="to-customize-the-beforelayout-target"></a>Pour personnaliser la cible BeforeLayout

1. Ouvrez un éditeur, tel que le bloc-notes, puis ajoutez le code suivant.

   ```xml
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Target Name="BeforeLayout">
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>
     </Target>
   </Project>
   ```

    Cet exemple affiche un message avant l’empaquetage de cette cible.

2. Nommez le fichier **customlayout. SharePoint. targets**, puis enregistrez-le dans le dossier du projet SharePoint.

3. Ouvrez le projet, ouvrez le menu contextuel, puis choisissez **décharger le projet**.

4. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **modifier** *\<ProjectName> . vbproj* ou **Edit** *\<ProjectName> . csproj*.

5. Après la `Import` ligne près de la fin du fichier projet, ajoutez la ligne suivante.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. Enregistrez et fermez le fichier projet.

7. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **recharger le projet**.

   Lorsque vous publiez le projet, le message s’affiche dans la sortie avant le début de l’empaquetage.

#### <a name="to-customize-the-afterlayout-target"></a>Pour personnaliser la cible AfterLayout

1. Dans la barre de menus, choisissez **fichier**  >  **ouvrir** un  >  **fichier**.

2. Dans la boîte de dialogue **ouvrir un fichier** , accédez au dossier du projet, choisissez le fichier customlayout. Target, puis cliquez sur le bouton **ouvrir** .

3. Juste avant la `</Project>` balise, ajoutez le code suivant :

   ```xml
   <Target Name="AfterLayout">
     <Message Importance="high" Text="In the AfterLayout Target"></Message>
   </Target>
   ```

    Cet exemple affiche un message après que cette cible a été empaquetée.

4. Enregistrez et fermez le fichier de cibles.

5. Redémarrez Visual Studio, puis ouvrez le projet.

   Lorsque vous publiez le projet, le message BeforeLayout s’affiche avant le démarrage de l’empaquetage et le message AfterLayout s’affiche après la fin de l’empaquetage.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
