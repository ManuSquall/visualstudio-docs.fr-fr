---
title: Galeries privées (en anglais) Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 895fbef5459de75c7ccdc6a090fc30ec27a030f9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444919"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez partager les contrôles, les modèles et les outils que vous développez en les affichant dans une *galerie privée* sur l’intranet pour votre organisation, comme suit :  
  
- Créez un flux Atom (RSS) à un emplacement central configuré (référentiel) sur votre intranet. Pour plus d’informations, voir [Comment : Créer un flux d’atome pour une galerie privée](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
- Distribuez un fichier .pkgdef qui décrit la galerie privée. Nous recommandons cette configuration pour les administrateurs qui veulent connecter une galerie privée à de nombreux ordinateurs en même temps.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Ajout d’une galerie privée aux extensions et mises à jour dans Visual Studio  
 Lorsqu’une galerie privée est disponible, vous pouvez l’ajouter à **Extensions et Mises à jour** dans Visual Studio.  
  
 ![Boîte de dialogue d'ajout de gestionnaire d'extensions](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Pour ajouter une galerie privée aux extensions et mises à jour  
  
1. Sur la barre de menu, choisissez **Des outils,** **options**.  
  
2. Dans le nœud **environnement,** sélectionnez **Extensions et Mises à jour**.  
  
3. Choisissez le bouton **Ajouter**.  
  
4. Dans le champ **Name,** entrez un nom `My Gallery`pour la galerie privée, par exemple, .  
  
5. Dans le champ **URL,** entrez l’URL du flux Atom ou du site SharePoint qui héberge la galerie privée.  
  
    1. Si l’hôte est un flux Atom qui se connecte à `http://www.mywebsite/mygallery/atom.xml`la galerie privée, l’URL ressemblerait à celle-ci: .  Cette URL peut se référer à un fichier ou à un chemin réseau.  
  
    2. Si l’hôte est un site SharePoint, `http://mysharepoint/sites/mygallery/forms/AllItems.aspx`l’URL ressemblerait à celui-ci: .  
  
### <a name="managing-private-galleries"></a>Gestion des galeries privées  
 Un administrateur peut mettre une galerie privée à la disposition de plusieurs ordinateurs en même temps en modifiant le registre du système sur chaque ordinateur. Pour ce faire, créez un fichier .pkgdef qui décrit les nouvelles clés de registre et leurs valeurs.  Le format de ce fichier est le suivant.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Pour plus d’informations, voir [Comment gérer une galerie privée en utilisant les paramètres du registre](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Installation d’extensions à partir d’une galerie privée  
 Vous pouvez rechercher et installer des extensions Visual Studio à partir d’une galerie privée dans **Extensions and Updates**. Les étapes suivantes utilisent `My Gallery`une galerie privée nommée .  
  
 ![Galerie privée d'installation du gestionnaire d'extensions](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Rechercher et installer des extensions à partir d’une galerie privée  
  
1. Dans la barre de menus, choisissez **Outils**, puis **Extensions et mises à jour**.  
  
2. Dans la vitre gauche, sélectionnez **extensions en ligne,** puis sélectionnez **My Gallery**.  
  
3. Dans le volet droit, sélectionnez une extension, puis choisissez le bouton **Télécharger.**  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Mise à jour des extensions d’une galerie privée  
 Comme de nouvelles versions d’extensions Visual Studio sont affichées dans la galerie privée, vous pouvez mettre à jour les extensions que vous avez installées. Les étapes suivantes utilisent `My Repository`une galerie privée nommée .  
  
 ![Mise à jour de la galerie privée du gestionnaire d’extensions](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Mettre à jour une extension installée à partir d’une galerie privée  
  
1. Dans la barre de menus, choisissez **Outils**, puis **Extensions et mises à jour**.  
  
2. Dans la vitre gauche, sélectionnez **mises à jour,** puis sélectionnez **Mon Dépôt**.  
  
3. Dans le volet droit, sélectionnez une extension, puis choisissez le bouton **Mise à jour.**  
  
## <a name="see-also"></a>Voir aussi  
 [Trouver et utiliser des extensions de studio visuel](../ide/finding-and-using-visual-studio-extensions.md)   
 [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
