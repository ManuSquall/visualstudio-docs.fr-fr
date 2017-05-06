---
title: "Comment&#160;: personnaliser une fonctionnalit&#233; SharePoint"
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
  - "VS.SharePointTools.RAD.FeatureDesigner.SwitchView"
  - "VS.SharePointTools.RAD.featureDesigner.Manifest"
  - "VS.SharePointTools.RAD.FeatureDesignerProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, fonctionnalités"
ms.assetid: e624c546-564b-4c73-9f1b-dc3675e76a55
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Comment&#160;: personnaliser une fonctionnalit&#233; SharePoint
  Vous pouvez créer et personnaliser des fonctionnalités SharePoint en utilisant le Concepteur de fonctionnalités dans Visual Studio.  Il est possible, par exemple, de définir la portée de la fonctionnalité et d'ajouter d'autres fonctionnalités comme dépendances.  Par défaut, le Concepteur de fonctionnalités s'ouvre dès que vous ajoutez une nouvelle fonctionnalité dans l'Explorateur de solutions ou dans l'Explorateur de package SharePoint.  
  
## Ouverture du Concepteur de fonctionnalités  
 Vous pouvez ajouter ou supprimer des éléments de projet SharePoint d'une fonctionnalité à l'aide du Concepteur de fonctionnalités.  
  
#### Pour ouvrir le Concepteur de fonctionnalités  
  
1.  Dans l'**Explorateur de solutions**, développez **Fonctionnalités**.  
  
2.  Double\-cliquez sur l'élément *Feature1*, ou ouvrez le menu contextuel de l'élément *Feature1* puis choisissez **Concepteur de vues**.  
  
## Consultation du fichier manifeste ajouté au package  
 Vous pouvez faire appel au Concepteur de fonctionnalités pour modifier et générer le fichier manifeste ajouté au package pour la fonctionnalité \(feature.xml\),  puis consulter le code XML de ce fichier à partir de Visual Studio.  
  
#### Pour consulter le fichier manifeste ajouté au package  
  
1.  Dans le **Composant de composant**, choisissez l'onglet **Manifeste**.  
  
#### Pour consulter le fichier manifeste ajouté au package, au moyen de l'Explorateur de solutions  
  
1.  Dans l'**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.  
  
2.  Développez Feature, développez FeatureName, développez FeatureName.feature, puis ouvrez ensuite le fichier *FeatureName*. Template.xml  
  
    > [!NOTE]  
    >  Lorsque vous ouvrez le fichier manifeste XML du modèle de fonctionnalité, les fichiers sont validés automatiquement et les avertissements éventuellement affichés dans la fenêtre Liste d'erreurs peuvent être ignorés.  
  
## Modification du modèle de manifeste  
 Vous pouvez modifier le code XML du fichier manifeste de la fonctionnalité à partir de l'éditeur XML de Visual Studio ou du volet Modèle de manifeste.  Tous les changements apportés au code XML sont fusionnés dans le fichier manifeste ajouté au package pour la fonctionnalité.  Il pourrait être intéressant, par exemple, de modifier le modèle de manifeste en vue de personnaliser une propriété Fonctionnalité.  
  
#### Pour modifier le modèle de manifeste à l'aide de l'éditeur XML  
  
1.  Dans le **Concepteur de fonctionnalité**, choisissez l'onglet **Manifeste**, développez le nœud **Options d’édition**, puis choisissez le lien **Ouvrir dans l'éditeur XML**.  
  
     Les changements apportés au code XML sont fusionnés dans le fichier manifeste ajouté au package.  
  
#### Pour modifier le modèle de manifeste à partir du volet Modèle de manifeste  
  
1.  Dans le **concepteur de composants**, choisissez l'onglet **Manifeste**, développez le nœud **Options d’édition**, puis modifiez XML qui s'affiche dans le volet modèle de manifeste.  
  
     Les changements apportés au code XML sont visibles dans le volet **Aperçu du manifeste ajouté au package**.  
  
## Remplacement du fichier manifeste ajouté au package  
 Vous pouvez désactiver le Concepteur de fonctionnalités et créer le fichier feature.xml manuellement.  La première fois que vous procédez ainsi, les paramètres actuellement définis dans le Concepteur de fonctionnalités sont enregistrés dans le fichier XML du modèle de fonctionnalité.  Ill suffit ensuite de modifier ou de remplacer le code XML.  
  
> [!NOTE]  
>  Si vous ajoutez ou supprimez des éléments de projet SharePoint dans le fichier XML alors que le Concepteur de fonctionnalités est désactivé, ces actions ne sont pas prises en compte dans le package.  
  
#### Pour remplacer le fichier manifeste ajouté au package en désactivant le concepteur  
  
1.  Dans le **Composant de composant**, choisissez l'onglet **Manifeste**.  
  
2.  Développez le nœud **Options d’édition**, choisissez le lien **Remplacez le code XML généré et modifiez le manifeste dans l'éditeur XML**, puis cliquez sur le bouton **Oui**.  
  
     Le modèle est mis à jour en fonction du fichier manifeste ajouté au package.  
  
## Activation du Concepteur de fonctionnalités  
 Vous pouvez réactiver le Concepteur de fonctionnalités pour personnaliser le fichier feature.xml.  
  
#### Pour réactiver le concepteur  
  
1.  Dans le **Concepteur de composant**, sélectionnez le lien **Ignorer les modifications manifestes et réactiver le concepteur**, puis cliquez sur le bouton **Oui**.  
  
2.  Le modèle est actualisé en fonction du texte d'origine et toutes les modifications apportées au code XML sont perdues.  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  