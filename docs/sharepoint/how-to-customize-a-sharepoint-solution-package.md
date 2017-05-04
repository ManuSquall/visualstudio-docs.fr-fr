---
title: "Comment&#160;: personnaliser un package de solution SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.RAD.PackageDesignerAdvanced"
  - "VS.SharePointTools.RAD.PackageDesigner.Manifest"
  - "VS.SharePointTools.RAD.PackageDesignerProperties"
  - "VS.SharePointTools.RAD.PackageDesigner.SwitchView"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, packages"
ms.assetid: fd365f8c-8a80-4ce8-8e28-c0eb609f12f3
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Comment&#160;: personnaliser un package de solution SharePoint
  Vous pouvez vous servir du Concepteur de packages pour créer et personnaliser un package \(.wsp\).  Pourquoi pas, par exemple, ajouter des éléments de projet SharePoint et des fonctionnalités, provoquer ou non la réinitialisation du serveur Web lors du déploiement de la solution et configurer le type de serveur de déploiement ?  
  
## Ouverture du Concepteur de packages  
  
#### Pour ouvrir le Concepteur de packages  
  
-   Dans **Explorateur de solutions**, double\-cliquez sur **Package**, ou choisissez **Concepteur de vues** dans le menu contextuel de **Package**.  
  
## Consultation du fichier manifeste ajouté au package  
 Vous pouvez faire appel au Concepteur de packages pour modifier et générer le fichier manifeste ajouté au package,  puis consulter le code XML de ce fichier à partir de Visual Studio.  
  
#### Pour afficher le fichier source XML  
  
1.  Dans **Concepteur de packages**, choisissez **Manifeste**.  
  
#### Pour consulter le fichier manifeste ajouté au package, au moyen de l'Explorateur de solutions  
  
1.  Dans **Explorateur de solutions**, choisissez **Afficher tous les fichiers**.  
  
2.  Développez le package, développez Package.package, puis ouvrez le fichier Package.Template.xml.  
  
    > [!NOTE]  
    >  Lorsque vous ouvrez le fichier manifeste XML du modèle du package, les fichiers sont validés automatiquement et les avertissements éventuellement affichés dans la fenêtre Liste d'erreurs peuvent être ignorés.  
  
## Modification du modèle de manifeste  
 Vous pouvez modifier le code XML du fichier manifeste ajouté au package à partir de l'éditeur XML de Visual Studio ou du volet Modèle de manifeste.  Tous les changements apportés au code XML sont fusionnés dans le fichier manifeste ajouté au package pour le package.  
  
#### Pour modifier le modèle de manifeste à l'aide de l'éditeur XML  
  
1.  Dans le **Concepteur de Package**, choisissez l'onglet **Manifeste**, développez le nœud **Options d’édition**, puis choisissez le lien **Ouvrir dans l'éditeur XML**.  
  
     Les changements apportés au code XML sont fusionnés dans le fichier manifeste ajouté au package.  
  
#### Pour modifier le modèle de manifeste à partir du volet Modèle de manifeste  
  
1.  Dans le **Concepteur de Package**, choisissez l'onglet **Manifeste**, développez le nœud **Options d’édition**, puis modifiez XML qui s'affiche dans le volet modèle de manifeste.  
  
     Les changements apportés au code XML sont visibles dans le volet **Aperçu du manifeste ajouté au package**.  
  
## Remplacement du fichier manifeste ajouté au package  
 Vous pouvez désactiver le Concepteur de packages et créer le fichier manifest.xml manuellement.  La première fois que vous procédez ainsi, les paramètres actuellement définis dans le Concepteur de packages sont enregistrés dans le fichier XML du modèle de package.  Ill suffit ensuite de modifier ou de remplacer le code XML.  
  
> [!NOTE]  
>  Si vous ajoutez ou supprimez des éléments de projet SharePoint et des fonctionnalités dans le fichier XML alors que le Concepteur de packages est désactivé, ces actions ne sont pas prises en compte dans le package.  
  
#### Pour remplacer le fichier manifeste ajouté au package en désactivant le concepteur  
  
1.  Dans le **Concepteur de Package**, choisissez l'onglet **Manifeste**.  
  
2.  .  
  
3.  Développez le nœud **Options d’édition**, choisissez le lien **Remplacez le code XML généré et modifiez le manifeste dans l'éditeur XML**, puis cliquez sur le bouton **Oui**.  
  
     Le modèle est mis à jour en fonction du fichier manifeste ajouté au package.  
  
## Activation du Concepteur de packages  
 Vous pouvez réactiver le Concepteur de packages pour personnaliser le fichier manifest.xml.  
  
#### Pour réactiver le concepteur  
  
1.  Dans le **Concepteur de package**, sélectionnez le lien **Ignorer les modifications manifestes et réactiver le concepteur**, puis cliquez sur le bouton **Oui**.  
  
     Le modèle est actualisé en fonction du texte d'origine et toutes les modifications apportées au code XML sont perdues.  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  