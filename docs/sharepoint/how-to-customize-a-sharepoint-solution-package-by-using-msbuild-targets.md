---
title: Personnaliser le package de solution SharePoint à l’aide de cibles de MSBuild
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71665f6ccf22ace264ff39831521538a335aed93
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401506"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Procédure : Personnaliser un package de SharePoint Solution à l’aide de cibles de MSBuild
  À l’aide de cibles MSBuild à l’invite de commande, vous pouvez personnaliser la façon dont Visual Studio crée les fichiers de package SharePoint ( *.wsp*). Par exemple, vous pouvez personnaliser les propriétés MSBuild pour modifier le répertoire intermédiaire d’empaquetage et les groupes d’éléments MSBuild qui spécifient les fichiers énumérés.

## <a name="customize-and-run-msbuild-targets"></a>Personnaliser et exécuter des cibles de MSBuild
 Si vous personnalisez les cibles BeforeLayout et AfterLayout, vous pouvez effectuer des tâches avant la disposition du package, telles que l’ajout, suppression ou modification des fichiers qui sont empaquetés.

#### <a name="to-customize-the-beforelayout-target"></a>Pour personnaliser la cible BeforeLayout

1. Ouvrir un éditeur, tel que le bloc-notes et puis ajoutez le code suivant.

   ```xml
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Target Name="BeforeLayout">
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>
     </Target>
   </Project>
   ```

    Cet exemple affiche un message avant de l’empaquetage de cette cible.

2. Nommez le fichier **CustomLayout.SharePoint.targets**, puis enregistrez-le dans le dossier du projet SharePoint.

3. Ouvrez le projet, ouvrez son menu contextuel, puis choisissez **décharger le projet**.

4. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **modifier**  *\<nom_projet > .vbproj* ou **modifier**  *\<Nom_projet > .csproj*.

5. Après le `Import` ligne vers la fin du fichier projet, ajoutez la ligne suivante.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. Enregistrez et fermez le fichier de projet.

7. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **recharger le projet**.

   Lorsque vous publiez le projet, le message s’affiche dans la sortie avant le début de l’empaquetage.

#### <a name="to-customize-the-afterlayout-target"></a>Pour personnaliser la cible AfterLayout

1. Dans la barre de menus, choisissez **fichier** > **Open** > **fichier**.

2. Dans le **ouvrir un fichier** boîte de dialogue, accédez au dossier du projet, choisissez le fichier CustomLayout.target, puis le **Open** bouton.

3. Juste avant la `</Project>` , ajoutez le code suivant :

   ```xml
   <Target Name="AfterLayout">
     <Message Importance="high" Text="In the AfterLayout Target"></Message>
   </Target>
   ```

    Cet exemple affiche un message une fois que cette cible est empaquetée.

4. Enregistrez et fermez le fichier de cibles.

5. Redémarrez Visual Studio et ouvrez le projet.

   Lorsque vous publiez le projet, le message BeforeLayout apparaît avant le début de l’empaquetage, et le AfterLayout message une fois terminée de l’empaquetage.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
