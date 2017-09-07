---
title: "Galeries privées | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 8ce054bf6149f0224785f4c3cd9274e86dc09d04
ms.openlocfilehash: e4c49a19a9befad5d90b9526842786f49af0851b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="private-galleries"></a>Private Galleries
Vous pouvez partager des contrôles, des modèles et des outils que vous développez en les envoyant à un *galerie privée* sur l’intranet de votre organisation, comme suit :  
  
-   Créer un flux dans un emplacement central (référentiel) configuré correctement sur votre intranet Atom (RSS). Pour plus d’informations, consultez [Comment : créer un flux Atom pour une galerie privée](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Distribuer un fichier .pkgdef qui décrit la galerie privée. Nous recommandons cette configuration pour les administrateurs qui souhaitent se connecter une galerie privée à de nombreux ordinateurs en même temps.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Ajout d’une galerie privée aux Extensions et mises à jour dans Visual Studio  
 Lorsqu’une galerie privée est disponible, vous pouvez l’ajouter à **Extensions et mises à jour** dans Visual Studio.  
  
 ![Gestionnaire d’extensions de boîte de dialogue Ajouter](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Pour ajouter une galerie privée aux Extensions et mises à jour  
  
1.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  
  
2.  Dans le **environnement** nœud, sélectionnez **Extensions et mises à jour**.  
  
3.  Choisissez le bouton **Ajouter** .  
  
4.  Dans le **nom** , entrez un nom pour la galerie privée, par exemple, `My Gallery`.  
  
5.  Dans le **URL** , entrez l’URL du flux Atom ou du site SharePoint qui héberge la galerie privée.  
  
    1.  Si l’hôte est un flux Atom qui se connecte à la galerie privée, l’URL ressemble à celle-ci : http://www.mywebsite/mygallery/atom.xml.  Cette URL peut faire référence à un fichier ou un chemin d’accès réseau.  
  
    2.  Si l’hôte est un site SharePoint, l’URL ressemble à celle-ci : http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>La gestion des galeries privées  
 Un administrateur peut rendre une galerie privée disponible pour plusieurs ordinateurs en même temps en modifiant le Registre système sur chaque ordinateur. Pour ce faire, créez un fichier .pkgdef qui décrit les nouvelles clés de Registre et leurs valeurs.  Le format de ce fichier est comme suit.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Pour plus d’informations, consultez [Comment : gérer une privée galerie par à l’aide de paramètres de Registre](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Installation des Extensions à partir d’une galerie privée  
 Vous pouvez rechercher et installer des extensions Visual Studio à partir d’une galerie privée dans **Extensions et mises à jour**. La procédure suivante utilise une galerie privée nommée `My Gallery`.  
  
 ![Gestionnaire d’extensions de l’installation de galerie privée](../extensibility/media/em_.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Pour rechercher et installer des extensions à partir d’une galerie privée  
  
1.  Dans la barre de menus, choisissez **Outils**, puis **Extensions et mises à jour**.  
  
2.  Dans le volet gauche, sélectionnez **Extensions en ligne**, puis sélectionnez **mes galerie**.  
  
3.  Dans le volet droit, sélectionnez une extension, puis choisissez le **télécharger** bouton.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Mise à jour des Extensions à partir d’une galerie privée  
 Comme les nouvelles versions des extensions Visual Studio sont validées dans la galerie privée, vous pouvez mettre à jour les extensions que vous avez installée. La procédure suivante utilise une galerie privée nommée `My Repository`.  
  
 ![Mise à jour de la galerie privée du Gestionnaire d’extensions](../extensibility/media/em_update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Pour mettre à jour une extension installée à partir d’une galerie privée  
  
1.  Dans la barre de menus, choisissez **Outils**, puis **Extensions et mises à jour**.  
  
2.  Dans le volet gauche, sélectionnez **mises à jour**, puis sélectionnez **mon référentiel**.  
  
3.  Dans le volet droit, sélectionnez une extension, puis choisissez le **mise à jour** bouton.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et utilisation des Extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
