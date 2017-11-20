---
title: "Comment : personnaliser une fonctionnalité SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, features
ms.assetid: e624c546-564b-4c73-9f1b-dc3675e76a55
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d81a65a8030fd77ead1362602b0e16f474ef410c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Comment : personnaliser une fonctionnalité SharePoint
  Vous pouvez créer et personnaliser des fonctionnalités SharePoint à l’aide du Concepteur de fonctionnalités dans Visual Studio. Par exemple, vous pouvez définir l’étendue de la fonctionnalité et ajouter d’autres fonctionnalités en tant que dépendances. Par défaut, le Concepteur de fonctionnalités est ouvert lorsque vous ajoutez une nouvelle fonctionnalité dans l’Explorateur de solutions ou l’Explorateur de Package SharePoint.  
  
## <a name="opening-the-feature-designer"></a>Ouverture du Concepteur de fonctionnalités  
 Vous pouvez ajouter ou supprimer des éléments de projet SharePoint à une fonctionnalité à l’aide du Concepteur de fonctionnalités.  
  
#### <a name="to-open-the-feature-designer"></a>Pour ouvrir le Concepteur de fonctionnalités  
  
1.  Dans **l’Explorateur de solutions**, développez **fonctionnalités**.  
  
2.  Double-cliquez sur le *Feature1* d’élément, ou ouvrez le menu contextuel pour le *Feature1* d’élément, puis choisissez **Concepteur de vue**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Affichage du fichier manifeste du package  
 Vous pouvez utiliser le Concepteur de fonctionnalités pour modifier et générer le fichier manifeste de package pour la fonctionnalité (feature.xml). Ensuite, vous pouvez afficher le code XML de ce fichier dans Visual Studio.  
  
#### <a name="to-view-the-packaged-manifest-file"></a>Pour consulter le fichier manifest de package  
  
1.  Dans le **Concepteur de fonctionnalités**, choisissez le **manifeste** onglet.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Pour afficher le fichier manifeste de package à l’aide de l’Explorateur de solutions  
  
1.  Dans **l’Explorateur de solutions**, choisissez le **afficher tous les fichiers** icône.  
  
2.  Développez des fonctionnalités, développez NomFonctionnalité, développez FeatureName.feature, puis ouvrez le *FeatureName*. Fichier Template.Xml.  
  
    > [!NOTE]  
    >  Lorsque vous ouvrez le fichier XML de manifeste de modèle de fonction, les fichiers sont validés automatiquement et les avertissements qui apparaissent dans la fenêtre liste d’erreurs peuvent être ignorés.  
  
## <a name="changing-the-manifest-template"></a>Modifier le modèle de manifeste  
 Vous pouvez modifier le code XML pour le fichier de manifeste de fonctionnalité dans l’éditeur XML de Visual Studio ou dans le volet modèle de manifeste. Toutes les modifications au code XML est fusionné dans le fichier manifest de package pour la fonctionnalité. Par exemple, vous souhaiterez modifier le modèle de manifeste pour personnaliser une propriété de fonctionnalité.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Pour modifier le modèle de manifeste à l’aide de l’éditeur XML  
  
1.  Dans le **Concepteur de fonctionnalités**, choisissez le **manifeste** onglet, développez le **modifier les Options** nœud, puis choisissez le **ouvert dans l’éditeur XML** lien.  
  
     Modifications apportées au document XML sont fusionnées dans le fichier manifest de package.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Pour modifier le modèle de manifeste à l’aide du volet modèle de manifeste  
  
1.  Dans le **Concepteur de fonctionnalités**, choisissez le **manifeste** onglet, développez le **modifier les Options** nœud et modifiez le code XML qui s’affiche dans le volet modèle de manifeste.  
  
     Affichage des modifications au code XML dans le **aperçu du manifeste ajouté au package** volet.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Remplacement du fichier manifeste du package  
 Vous pouvez désactiver le Concepteur de fonctionnalités et créer le fichier feature.xml manuellement. La première fois que vous procédez ainsi, les paramètres actuels dans le Concepteur de fonctionnalités sont enregistrées au fichier XML de modèle de fonction. Ensuite, vous pouvez modifier ou remplacer le code XML.  
  
> [!NOTE]  
>  Si vous ajoutez ou supprimez des éléments de projet SharePoint dans le fichier XML alors que le Concepteur de fonctionnalités est désactivé, ces éléments de projet ne sont pas compressées.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Pour remplacer le fichier manifest de package en désactivant le Concepteur  
  
1.  Dans le **Concepteur de fonctionnalités**, choisissez le **manifeste** onglet.  
  
2.  Développez le **modifier les Options** nœud, choisissez le **remplacer généré XML et modifier le manifeste dans l’éditeur XML** lier, puis choisissez le **Oui** bouton.  
  
     Le modèle est mis à jour avec le fichier de manifeste de package en cours.  
  
## <a name="enabling-the-feature-designer"></a>L’activation du Concepteur de fonctionnalités  
 Vous pouvez réactiver le Concepteur de fonctionnalités pour personnaliser le fichier feature.xml.  
  
#### <a name="to-re-enable-the-designer"></a>Pour réactiver le Concepteur  
  
1.  Dans le **Concepteur de fonctionnalités**, choisissez le **ignorer modifications du manifeste et réactivez le concepteur** lier, puis choisissez le **Oui** bouton.  
  
2.  Le modèle est actualisé avec le texte d’origine et les modifications au code XML sont perdues.  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  