---
title: 'Comment : personnaliser une fonctionnalité SharePoint | Microsoft Docs'
description: Personnaliser les fonctionnalités SharePoint dans Visual Studio. Le concepteur de fonctionnalités s’ouvre lorsque vous ajoutez une nouvelle fonctionnalité dans Explorateur de solutions ou dans l’Explorateur de package SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4846d79af7a031970e8870626f88450e8a3e647
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903661"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Comment : personnaliser une fonctionnalité SharePoint
  Vous pouvez créer et personnaliser des fonctionnalités SharePoint à l’aide du concepteur de fonctionnalités dans Visual Studio. Par exemple, vous pouvez définir l’étendue de la fonctionnalité et ajouter d’autres fonctionnalités en tant que dépendances. Par défaut, le concepteur de fonctionnalités s’ouvre lorsque vous ajoutez une nouvelle fonctionnalité dans Explorateur de solutions ou dans l’Explorateur de package SharePoint.

## <a name="opening-the-feature-designer"></a>Ouverture du concepteur de fonctionnalités
 Vous pouvez ajouter ou supprimer des éléments de projet SharePoint à une fonctionnalité à l’aide du concepteur de fonctionnalités.

#### <a name="to-open-the-feature-designer"></a>Pour ouvrir le concepteur de fonctionnalités

1. Dans **Explorateur de solutions**, développez **fonctionnalités**.

2. Double-cliquez sur l’élément *Feature1* , ou ouvrez le menu contextuel de l’élément *Feature1* , puis choisissez **Concepteur de vues**.

## <a name="view-the-packaged-manifest-file"></a>Afficher le fichier manifeste empaqueté
 Vous pouvez utiliser le concepteur de fonctionnalités pour modifier et générer le fichier manifeste empaqueté pour la fonctionnalité (*feature.xml*). Ensuite, vous pouvez afficher le code XML de ce fichier dans Visual Studio.

#### <a name="to-view-the-packaged-manifest-file"></a>Pour afficher le fichier manifeste empaqueté

1. Dans le **Concepteur de fonctionnalités**, choisissez l’onglet **manifeste** .

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Pour afficher le fichier manifeste empaqueté à l’aide de Explorateur de solutions

1. Dans **Explorateur de solutions**, choisissez l’icône **Afficher tous les fichiers** .

2. Développez fonctionnalités, puis NomFonctionnalité et NomFonctionnalité. Feature, puis ouvrez le fichier *\<FeatureName>.Template.xml* .

    > [!NOTE]
    > Lorsque vous ouvrez le fichier manifeste XML du modèle de fonctionnalité, les fichiers sont validés automatiquement et les avertissements qui s’affichent dans la fenêtre de Liste d’erreurs peuvent être ignorés.

## <a name="change-the-manifest-template"></a>Modifier le modèle de manifeste
 Vous pouvez modifier le code XML du fichier manifeste de fonctionnalité dans l’éditeur XML de Visual Studio ou dans le volet modèle de manifeste. Toutes les modifications apportées au code XML sont fusionnées dans le fichier manifeste empaqueté pour la fonctionnalité. Par exemple, vous souhaiterez peut-être modifier le modèle de manifeste pour personnaliser une propriété de fonctionnalité.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Pour modifier le modèle de manifeste à l’aide de l’éditeur XML

1. Dans le **Concepteur de fonctionnalités**, choisissez l’onglet **manifeste** , développez le nœud **options de modification** , puis cliquez sur le lien **ouvrir dans l’éditeur XML** .

     Les modifications apportées au code XML sont fusionnées dans le fichier manifeste empaqueté.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Pour modifier le modèle de manifeste à l’aide du volet modèle de manifeste

1. Dans le **Concepteur de fonctionnalités**, choisissez l’onglet **manifeste** , développez le nœud **options de modification** , puis modifiez le XML qui s’affiche dans le volet modèle de manifeste.

     Les modifications apportées au XML s’affichent dans le volet **Aperçu du manifeste du package** .

## <a name="overwrite-the-packaged-manifest-file"></a>Remplacer le fichier manifeste empaqueté
 Vous pouvez désactiver le concepteur de fonctionnalités et créer le fichier *feature.xml* manuellement. La première fois que vous effectuez cette procédure, les paramètres actuels du concepteur de fonctionnalités sont enregistrés dans le fichier XML du modèle de fonctionnalité. Ensuite, vous pouvez modifier ou remplacer le code XML.

> [!NOTE]
> Si vous ajoutez ou supprimez des éléments de projet SharePoint dans le fichier XML alors que le concepteur de fonctionnalités est désactivé, ces éléments de projet ne sont pas empaquetés.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Pour remplacer le fichier manifeste empaqueté en désactivant le concepteur

1. Dans le **Concepteur de fonctionnalités**, choisissez l’onglet **manifeste** .

2. Développez le nœud **options de modification** , choisissez le lien remplacer le fichier **XML généré et modifier le manifeste dans l’éditeur XML** , puis choisissez le bouton **Oui** .

     Le modèle est mis à jour avec le fichier manifeste empaqueté actuel.

## <a name="enable-the-feature-designer"></a>Activer le concepteur de fonctionnalités
 Vous pouvez réactiver le concepteur de fonctionnalités pour personnaliser le fichier *feature.xml* .

#### <a name="to-re-enable-the-designer"></a>Pour réactiver le concepteur

1. Dans le **Concepteur de fonctionnalités**, choisissez le lien **Ignorer les modifications du manifeste et réactiver le concepteur** , puis choisissez le bouton **Oui** .

2. Le modèle est actualisé avec le texte d’origine et toute modification apportée au code XML est perdue.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
