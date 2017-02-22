---
title: "Les galeries priv&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Galeries VSIX, privés"
  - "galeries privées, VSIX"
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Les galeries priv&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez partager des contrôles, des modèles et des outils que vous développez en les envoyant à un *Galerie privée* sur l’intranet de votre organisation, comme suit :  
  
-   Créer un flux vers un emplacement central \(référentiel\) configuré correctement sur votre intranet Atom \(RSS\). Pour plus d'informations, consultez [Comment : créer un atome de flux pour une galerie privée](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Distribuer un fichier .pkgdef qui décrit la galerie privée. Nous recommandons cette configuration pour les administrateurs qui souhaitent se connecter une galerie privée à de nombreux ordinateurs en même temps.  
  
## Ajout d’une galerie privée à Extensions et mises à jour dans Visual Studio  
 Lorsqu’une galerie privée est disponible, vous pouvez l’ajouter à **Extensions et mises à jour** dans Visual Studio.  
  
 ![Boîte de dialogue d'ajout de gestionnaire d'extensions](../extensibility/media/em_adddialog.png "EM\_AddDialog")  
  
#### Pour ajouter une galerie privée à Extensions et mises à jour  
  
1.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  
  
2.  Dans le **environnement** nœud, sélectionnez **Extensions et mises à jour**.  
  
3.  Choisissez le bouton **Ajouter**.  
  
4.  Dans le **nom** entrez un nom pour la galerie privée, par exemple, `My Gallery`.  
  
5.  Dans le **URL** entrez l’URL du site SharePoint qui héberge la galerie privée ou flux Atom.  
  
    1.  Si l’hôte est un flux Atom qui se connecte à la galerie privée, l’URL ressemblerait à celle\-ci : http:\/\/www.mywebsite\/mygallery\/atom.xml.  Cette URL peut faire référence à un fichier ou un chemin d’accès réseau.  
  
    2.  Si l’hôte est un site SharePoint, l’URL peut se présenter comme celui\-ci : http:\/\/mysharepoint\/sites\/mygallery\/forms\/AllItems.aspx.  
  
### La gestion des galeries privées  
 Un administrateur peut rendre une galerie privée disponible sur plusieurs ordinateurs en même temps en modifiant le Registre système sur chaque ordinateur. Pour ce faire, créez un fichier .pkgdef qui décrit les nouvelles clés de Registre et leurs valeurs.  Le format de ce fichier est comme suit.  
  
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
  
 Pour plus d'informations, consultez [Comment : gérer une galerie privée à l’aide des paramètres du Registre](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## Installation des Extensions à partir d’une galerie privée  
 Vous pouvez rechercher et installer des extensions Visual Studio à partir d’une galerie privée dans **Extensions et mises à jour**. Les étapes suivantes utilisent une galerie privée nommée `My Gallery`.  
  
 ![Galerie privée d'installation du gestionnaire d'extensions](../extensibility/media/em_.png "EM\_")  
  
#### Pour rechercher et installer des extensions à partir d’une galerie privée  
  
1.  Dans la barre de menus, choisissez **Outils**, **Extensions et mises à jour**.  
  
2.  Dans le volet gauche, sélectionnez **Extensions en ligne**, puis sélectionnez **Mes galerie**.  
  
3.  Dans le volet droit, sélectionnez une extension, puis choisissez le **télécharger** bouton.  
  
## Mise à jour des Extensions à partir d’une galerie privée  
 Comme les nouvelles versions des extensions Visual Studio sont validées dans la galerie privée, vous pouvez mettre à jour les extensions que vous avez installés. Les étapes suivantes utilisent une galerie privée nommée `My Repository`.  
  
 ![Mise à jour de la galerie privée du gestionnaire d'extensions](../extensibility/media/em_update.png "EM\_Update")  
  
#### Pour mettre à jour une extension installée à partir d’une galerie privée  
  
1.  Dans la barre de menus, choisissez **Outils**, **Extensions et mises à jour**.  
  
2.  Dans le volet gauche, sélectionnez **mises à jour**, puis sélectionnez **Mon référentiel**.  
  
3.  Dans le volet droit, sélectionnez une extension, puis choisissez le **mise à jour** bouton.  
  
## Voir aussi  
 [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Envoi des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)