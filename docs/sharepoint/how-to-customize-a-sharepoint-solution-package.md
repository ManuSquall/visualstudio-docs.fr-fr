---
title: "Comment : personnaliser un Package de Solution SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: fd365f8c-8a80-4ce8-8e28-c0eb609f12f3
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5351165320dd0ff2d8c130c64adeff7be45de6fb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Comment : personnaliser un package de solution SharePoint
  Vous pouvez utiliser le Concepteur de packages pour créer et personnaliser un package (.wsp). Par exemple, vous pouvez ajouter des éléments de projet SharePoint et des fonctionnalités, spécifiez si le serveur Web est réinitialisé lorsque la solution est déployée et définir le type de serveur de déploiement.  
  
## <a name="opening-the-package-designer"></a>Ouvrir le Concepteur de packages  
  
#### <a name="to-open-the-package-designer"></a>Pour ouvrir le Concepteur de packages  
  
-   Dans **l’Explorateur de solutions**, double-cliquez sur **Package**, ou choisissez **Concepteur de vue** dans le menu contextuel pour **Package**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Affichage du fichier manifeste du package  
 Vous pouvez utiliser le Concepteur de packages pour modifier et générer le fichier manifeste de package. Ensuite, vous pouvez afficher le code XML de ce fichier dans Visual Studio.  
  
#### <a name="to-view-the-xml-source-file"></a>Pour afficher le fichier source XML  
  
1.  Dans le **Concepteur de packages**, choisissez **manifeste**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Pour afficher le fichier manifeste de package à l’aide de l’Explorateur de solutions  
  
1.  Dans **l’Explorateur de solutions**, choisissez **afficher tous les fichiers**.  
  
2.  Développez le Package, développez le package, puis ouvrez le fichier Package.Template.xml.  
  
    > [!NOTE]  
    >  Lorsque vous ouvrez le fichier XML de manifeste pour le modèle de package, les fichiers sont validés automatiquement, et vous pouvez ignorer les avertissements qui apparaissent dans la fenêtre liste d’erreurs.  
  
## <a name="changing-the-manifest-template"></a>Modifier le modèle de manifeste  
 Vous pouvez modifier le code XML du fichier de manifeste du package dans l’éditeur XML de Visual Studio ou dans le volet modèle de manifeste. Toutes les modifications au code XML sont fusionnées dans le fichier manifest de package pour le package.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Pour modifier le modèle de manifeste à l’aide de l’éditeur XML  
  
1.  Dans le **Concepteur de packages**, choisissez le **manifeste** onglet, développez le **modifier les Options** nœud, puis choisissez le **ouvert dans l’éditeur XML** lien.  
  
     Modifications apportées au document XML sont fusionnées dans le fichier manifest de package.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Pour modifier le modèle de manifeste à l’aide du volet modèle de manifeste  
  
1.  Dans le **Concepteur de packages**, choisissez le **manifeste** onglet, développez le **modifier les Options** nœud et modifiez le code XML qui s’affiche dans le volet modèle de manifeste.  
  
     Affichage des modifications au code XML dans le **aperçu du manifeste ajouté au package** volet.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Remplacement du fichier manifeste du package  
 Vous pouvez désactiver le Concepteur de packages et créer le fichier manifest.xml manuellement. La première fois que vous procédez ainsi, les paramètres actuels dans le Concepteur de packages sont enregistrés dans le fichier XML du modèle package. Ensuite, vous pouvez modifier ou remplacer le code XML.  
  
> [!NOTE]  
>  Si vous ajoutez ou supprimez des éléments de projet SharePoint et des fonctionnalités dans le fichier XML alors que le Concepteur de packages est désactivé, ces éléments de projet et les fonctionnalités ne sont pas empaquetées.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Pour remplacer le fichier manifest de package en désactivant le Concepteur  
  
1.  Dans le **Concepteur de packages**, choisissez le **manifeste** onglet.  
  
2.  .  
  
3.  Développez le **modifier les Options** nœud, choisissez le **remplacer généré XML et modifier le manifeste dans l’éditeur XML** lier, puis choisissez le **Oui** bouton.  
  
     Le modèle est mis à jour avec le fichier de manifeste de package en cours.  
  
## <a name="enabling-the-package-designer"></a>L’activation du Concepteur de packages  
 Vous pouvez réactiver le Concepteur de packages pour personnaliser le fichier manifest.xml.  
  
#### <a name="to-re-enable-the-designer"></a>Pour réactiver le Concepteur  
  
1.  Dans le **Concepteur de packages**, choisissez le **ignorer modifications du manifeste et réactivez le concepteur** lier, puis choisissez le **Oui** bouton.  
  
     Le modèle est actualisé avec le texte d’origine et les modifications au code XML sont perdues.  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  