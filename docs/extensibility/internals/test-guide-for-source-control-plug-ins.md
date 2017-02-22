---
title: "Guide d&#39;&#233;valuation pour les Plug-ins de contr&#244;le de code Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plug-ins, contrôle de code source"
  - "contrôle de code source (Visual Studio SDK), plug-ins de test"
  - "tests, les plug-ins de contrôle de code source"
  - "test, plug-ins de contrôle de code source"
  - "contrôle plug-ins de source, guide de test"
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Guide d&#39;&#233;valuation pour les Plug-ins de contr&#244;le de code Source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette section fournit des conseils pour tester votre plug\-in contrôle de code source avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Une présentation complète des zones testantes les plus courantes, ainsi que certaines zones plus complexes qui peut être problématique est fournie.  Elle n'est pas vraiment être une liste exhaustive des cas de test.  
  
> [!NOTE]
>  Des résolutions de bogue et améliorations à dernier [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE peuvent découvrir des problèmes avec un existant le plug\-ins de contrôle de code source qui n'ont pas été précédemment produits lorsque vous utilisez des versions antérieures de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Il est fortement recommandé de tester votre plug\-in existant de contrôle de code source pour les zones énumérées dans cette section, même si aucune modification n'a été apportée au plug\-in depuis la version antérieure de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Préparation courante  
 un ordinateur avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et le plug\-in cible de contrôle de code source installé, est requis.  Un deuxième ordinateur également configuré peut être utilisé pour une partie de l'ouverture des tests de contrôle de code source.  
  
## définition des termes  
 Pour les besoins de ce guide de test, utilisez les définitions suivantes de terme :  
  
 projet client  
 Tout type de projet disponible dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qui prend en charge l'intégration du contrôle de code source \(par exemple, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], ou [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]\).  
  
 Projet Web  
 Il existe quatre types de projets Web : Système de fichiers, IIS locaux, sites distants, et FTP.  
  
-   Les projets de système de fichiers sont créés sur un chemin local, mais ils ne nécessitent pas les services \(IIS\) IIS à installer telle qu'ils sont accessibles en interne via un chemin d'accès UNC, et peuvent être placés sous contrôle de code source dans l'IDE, comme les projets clients.  
  
-   Travail de projets d'IIS de local avec IIS installé sur le même ordinateur et est l'accès à une URL pointant vers l'ordinateur local.  
  
-   Les projets de sites distants sont également créés sous des services IIS, mais ils sont placés sous contrôle de code source sur l'ordinateur de serveur IIS et non à partir de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE.  
  
-   Les projets FTP sont accessibles via un serveur FTP distant mais ils ne peuvent pas être placés sous contrôle de code source.  
  
 inscription  
 un autre terme pour la solution ou un projet sous le contrôle de code source.  
  
 Le magasin de version  
 La base de données contenant le contrôle de code source qui est accessible via l'API de plug\-in contrôle de code source.  
  
## Zones de test décrites dans cette section  
  
-   [Zone de test 1 : Ajouter \/ ouvrir à partir du contrôle de code Source](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   cas 1a : Ajouter la solution au contrôle de code source  
  
    -   cas 1B : solution ouverte de contrôle de code source  
  
    -   cas 1c : ajoutez la solution du contrôle de code source  
  
-   [Zone de test 2 : Obtenir à partir du contrôle de code Source](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Zone de test 3 : Extraire \/ annuler l’extraction](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Cas 3 : Contrôle\/extraction d'annulation  
  
    -   cas 3a : contrôle  
  
    -   cas 3b : extraction déconnectée  
  
    -   cas 3c : modification de requête\/sauvegarde de requête \(QEQS\)  
  
    -   cas 3d : Extraction silent  
  
    -   cas 3e : Extraction d'annulation  
  
-   [Zone de test 4 : Archiver](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   cas 4a : éléments modifiés  
  
    -   cas 4b : Ajout de fichiers  
  
    -   cas 4c : Ajout de projets  
  
-   [Zone de test 5 : Modifier le contrôle de Source](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   5a Cas : Liaison  
  
    -   cas 5b : Supprimez la liaison  
  
    -   cas 5c : Interface de nouveau\-vous  
  
-   [Test de zone 6: supprimer](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Test de zone 7: partage](../../extensibility/internals/test-area-7-share.md)  
  
-   [Test zone 8: Commutation plug\-in](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   cas 8a : modification automatique  
  
    -   cas 8b : modification Solution\-basée  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)