---
title: 'Comment : personnaliser une fonctionnalité SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9be9ba70bb94e743a788db11b55c188275bcad64
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118895"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Comment : personnaliser une fonctionnalité SharePoint
  Vous pouvez créer et personnaliser des fonctionnalités SharePoint à l’aide du Concepteur de fonctionnalités dans Visual Studio. Par exemple, vous pouvez définir l’étendue de fonctionnalité et ajouter d’autres fonctionnalités en tant que dépendances. Par défaut, le Concepteur de fonctionnalités s’ouvre lorsque vous ajoutez une nouvelle fonctionnalité dans l’Explorateur de solutions ou l’Explorateur de Package SharePoint.  
  
## <a name="opening-the-feature-designer"></a>Ouverture du Concepteur de fonctionnalités  
 Vous pouvez ajouter ou supprimer des éléments de projet SharePoint à une fonctionnalité à l’aide du Concepteur de fonctionnalités.  
  
#### <a name="to-open-the-feature-designer"></a>Pour ouvrir le Concepteur de fonctionnalités
  
1.  Dans **l’Explorateur de solutions**, développez **fonctionnalités**.  
  
2.  Double-cliquez sur le *Feature1* d’élément, ou ouvrez le menu contextuel pour le *Feature1* d’élément, puis choisissez **Concepteur de vues**.  
  
## <a name="view-the-packaged-manifest-file"></a>Consulter le fichier manifest de package  
 Vous pouvez utiliser le Concepteur de fonctionnalités pour modifier et générer le fichier manifeste de package pour la fonctionnalité (*feature.xml*). Ensuite, vous pouvez afficher le code XML de ce fichier dans Visual Studio.  
  
#### <a name="to-view-the-packaged-manifest-file"></a>Pour consulter le fichier manifest de package  
  
1.  Dans le **Concepteur de fonctionnalités**, choisissez le **manifeste** onglet.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Pour afficher le fichier manifeste de package à l’aide de l’Explorateur de solutions  
  
1.  Dans **l’Explorateur de solutions**, choisissez le **afficher tous les fichiers** icône.  
  
2.  Développez des fonctionnalités, développez FeatureName, développez FeatureName.feature, puis ouvrez le  *\<FeatureName >. Template.XML* fichier.  
  
    > [!NOTE]  
    >  Lorsque vous ouvrez le fichier XML de manifeste de modèle de fonctionnalité, les fichiers sont validés automatiquement et les avertissements qui apparaissent dans la fenêtre liste d’erreurs peuvent être ignorés.  
  
## <a name="change-the-manifest-template"></a>Modifier le modèle de manifeste  
 Vous pouvez modifier le code XML pour le fichier de manifeste de fonctionnalité dans l’éditeur XML de Visual Studio ou dans le volet modèle de manifeste. Toutes les modifications au code XML est fusionné dans le fichier manifest de package pour la fonctionnalité. Par exemple, vous souhaiterez modifier le modèle de manifeste pour personnaliser une propriété de fonctionnalité.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Pour modifier le modèle de manifeste à l’aide de l’éditeur XML  
  
1.  Dans le **Concepteur de fonctionnalités**, choisissez le **manifeste** onglet, développez le **modifier les Options** nœud, puis choisissez le **ouvert dans l’éditeur XML** lien.  
  
     Modifications apportées au document XML sont fusionnées dans le fichier manifest de package.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Pour modifier le modèle de manifeste en utilisant le volet modèle de manifeste  
  
1.  Dans le **Concepteur de fonctionnalités**, choisissez le **manifeste** onglet, développez le **modifier les Options** nœud et modifiez le code XML qui s’affiche dans le volet modèle de manifeste.  
  
     Modifications apportées au document XML s’affichent dans le **aperçu du manifeste ajouté au package** volet.  
  
## <a name="overwrite-the-packaged-manifest-file"></a>Remplacer le fichier manifeste de package  
 Vous pouvez désactiver le Concepteur de fonctionnalités et créer le *feature.xml* fichier manuellement. La première fois que vous procédez ainsi, les paramètres actuels dans le Concepteur de fonctionnalités sont enregistrées au fichier XML de modèle de fonctionnalité. Ensuite, vous pouvez modifier ou remplacer le code XML.  
  
> [!NOTE]  
>  Si vous ajoutez ou supprimez les éléments de projet SharePoint dans le fichier XML alors que le Concepteur de fonctionnalités est désactivé, ces éléments de projet ne sont pas compressées.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Pour remplacer le fichier manifest de package en désactivant le Concepteur  
  
1.  Dans le **Concepteur de fonctionnalités**, choisissez le **manifeste** onglet.  
  
2.  Développez le **modifier les Options** nœud, choisissez le **remplacement généré XML et modifier le manifeste dans l’éditeur XML** lier, puis choisissez le **Oui** bouton.  
  
     Le modèle est mis à jour avec le fichier de manifeste de package actuel.  
  
## <a name="enable-the-feature-designer"></a>Activer le Concepteur de fonctionnalités  
 Vous pouvez réactiver le Concepteur de fonctionnalités pour personnaliser le *feature.xml* fichier.  
  
#### <a name="to-re-enable-the-designer"></a>Pour réactiver le Concepteur  
  
1.  Dans le **Concepteur de fonctionnalités**, choisissez le **rejet modifications du manifeste et réactivez le concepteur** lier, puis choisissez le **Oui** bouton.  
  
2.  Le modèle est actualisée avec le texte d’origine, et les modifications au code XML sont perdues.  
  
## <a name="see-also"></a>Voir aussi
 [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
