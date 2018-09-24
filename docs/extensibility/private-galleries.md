---
title: Galeries privées | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e91b3ecec969ab6a717598d8dfb77e674890216a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638581"
---
# <a name="private-galleries"></a>Galeries privées
Vous pouvez partager des contrôles, des modèles et des outils que vous développez en les envoyant à un *galerie privée* sur l’intranet pour votre organisation, comme suit :  
  
-   Créer une source vers un emplacement central (référentiel) configuré correctement sur votre intranet Atom (RSS). Pour plus d’informations, consultez [Comment : créer un flux Atom pour une galerie privée](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Distribuer un *.pkgdef* fichier qui décrit la galerie privée. Nous recommandons cette configuration pour les administrateurs qui souhaitent se connecter une galerie privée à de nombreux ordinateurs en même temps.  
  
## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Ajouter une galerie privée aux extensions et mises à jour dans Visual Studio  
 Lorsqu’une galerie privée est disponible, vous pouvez l’ajouter à **Extensions et mises à jour** dans Visual Studio.  
  
 ![Gestionnaire d’extensions de boîte de dialogue Ajouter](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Pour ajouter une galerie privée aux Extensions et mises à jour  
  
1.  Dans la barre de menus, choisissez **Outils** > **Options**.  
  
2.  Dans le **environnement** nœud, sélectionnez **Extensions et mises à jour**.  
  
3.  Choisissez le bouton **Ajouter** .  
  
4.  Dans le **nom** , entrez un nom pour la galerie privée, par exemple, `My Gallery`.  
  
5.  Dans le **URL** , entrez l’URL du flux Atom ou du site SharePoint qui héberge la galerie privée.  
  
    1.  Si l’hôte est un flux Atom qui se connecte à la galerie privée, l’URL peut se présenter comme celle-ci : http://www.mywebsite/mygallery/atom.xml.  Cette URL peut faire référence à un fichier ou un chemin d’accès réseau.  
  
    2.  Si l’hôte est un site SharePoint, l’URL peut se présenter comme celle-ci : http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="manage-private-galleries"></a>Gérer les galeries privées  
 Un administrateur peut proposer une galerie privée à plusieurs ordinateurs en même temps en modifiant le Registre système sur chaque ordinateur. Pour ce faire, créez un *.pkgdef* fichier qui décrit les nouvelles clés de Registre et leurs valeurs.  Le format de ce fichier est le suivant.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Pour plus d’informations, consultez [Comment : gérer une galerie privée à l’aide de paramètres de Registre](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="install-extensions-from-a-private-gallery"></a>Installer des extensions à partir d’une galerie privée  
 Vous pouvez rechercher et installer des extensions Visual Studio à partir d’une galerie privée dans **Extensions et mises à jour**. Les étapes suivantes utilisent une galerie privée nommée `My Gallery`.  
  
 ![Gestionnaire d’extensions de l’installation de galerie privée](../extensibility/media/em_.png "EM_")  
  
### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Pour rechercher et installer des extensions à partir d’une galerie privée  
  
1.  Dans la barre de menus, choisissez **outils** > **Extensions et mises à jour**.  
  
2.  Dans le volet gauche, sélectionnez **des Extensions en ligne**, puis sélectionnez **ma galerie**.  
  
3.  Dans le volet droit, sélectionnez une extension, puis choisissez le **télécharger** bouton.  
  
## <a name="update-extensions-from-a-private-gallery"></a>Mettre à jour des extensions à partir d’une galerie privée  
 Comme les nouvelles versions des extensions Visual Studio sont publiées dans la galerie privée, vous pouvez mettre à jour les extensions que vous avez installée. Les étapes suivantes utilisent une galerie privée nommée `My Repository`.  
  
 ![Mise à jour de la galerie privée du Gestionnaire d’extension](../extensibility/media/em_update.png "EM_Update")  
  
### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Pour mettre à jour une extension installée à partir d’une galerie privée  
  
1.  Dans la barre de menus, choisissez **outils** > **Extensions et mises à jour**.  
  
2.  Dans le volet gauche, sélectionnez **mises à jour**, puis sélectionnez **mon référentiel**.  
  
3.  Dans le volet droit, sélectionnez une extension, puis choisissez le **mise à jour** bouton.  
  
## <a name="see-also"></a>Voir aussi  
 [Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Expédier les extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)