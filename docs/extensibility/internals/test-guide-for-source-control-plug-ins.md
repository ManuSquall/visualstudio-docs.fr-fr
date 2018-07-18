---
title: Guide de test de Plug-ins de contrôle de code Source | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 37af6a289b59b6066a71836e4d44e380b584ec70
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31145956"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guide de test de Plug-ins de contrôle de code Source
Cette section fournit des conseils pour le test de votre contrôle de source de plug-in avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Une vue d’ensemble complète de test les plus courants, ainsi que certaines zones plus complexes qui peuvent être problématiques est fournie. Cette vue d’ensemble n’est pas censée être une liste exhaustive des cas de test.  
  
> [!NOTE]
>  Certains correctifs de bogues et les améliorations apportées à la dernière version [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE peut révéler des problèmes avec la source contrôle plug-ins existants qui n’ont pas déjà été rencontrées lors de l’utilisation de versions précédentes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Il est fortement recommandé de tester votre contrôle de code source existant plug-in pour les zones sont énumérés dans cette section, même si aucune modification n’ont été apportées au plug-in depuis la version précédente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="common-preparation"></a>Préparation courantes  
 Un ordinateur avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et le plug-in de contrôle de source de cible d’installation, est requis. Un deuxième ordinateur configuré de la même façon peut servir pour une partie de l’ouvrir à partir de tests de contrôle de code Source.  
  
## <a name="definition-of-terms"></a>Définition des termes  
 Pour les besoins de ce guide de test, utilisez les définitions du terme suivantes :  
  
 Projet de client  
 Un projet de type disponible dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qui prend en charge l’intégration du contrôle source (par exemple, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], ou [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).  
  
 Projet Web  
 Il existe quatre types de projets Web : système de fichiers, serveur IIS Local, Sites distants et FTP.  
  
-   Projets de système de fichiers sont créés sur un chemin d’accès local, mais ils ne nécessitent pas l’Internet Informations Services (IIS) pour être installé qu’ils sont accessibles en interne via un chemin d’accès UNC et peuvent être placés sous contrôle de code source à partir d’à l’intérieur de l’IDE, comme les projets clients.  
  
-   Les projets IIS locaux fonctionnent avec IIS installé sur le même ordinateur et qui sont accessibles avec une URL pointant vers l’ordinateur local.  
  
-   Les projets de Sites distants sont également créés sous les Services IIS, mais ils sont placés sous contrôle de code source sur le serveur IIS et non à partir à l’intérieur de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
-   Projets FTP sont accessibles via un serveur FTP, mais ils ne peuvent pas être placés sous contrôle de code source.  
  
 Inscription  
 Un autre terme pour la solution ou un projet sous contrôle de code source.  
  
 La banque des versions  
 La base de contrôle de source qui est accessible via l’API de plug-in de contrôle de Source.  
  
## <a name="test-areas-covered-in-this-section"></a>Cette Section traitées des zones de test  
  
-   [Zone de test 1 : Ajouter / ouvrir à partir du contrôle de code Source](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Cas 1 : ajouter la Solution au contrôle de code Source  
  
    -   Cas 1 b : Ouvrez la Solution à partir du contrôle de code Source  
  
    -   Cas 1c : ajouter la Solution à partir du contrôle de code Source  
  
-   [Zone de test 2 : Obtenir à partir du contrôle de code source](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Zone de test 3 : Extraire / annuler l’extraction](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Cas 3 : Extraire / annuler l’extraction  
  
    -   Cas 3 : extraire  
  
    -   Cas 3 b : déconnecté d’extraction  
  
    -   Cas 3c : modifier la requête/requête enregistrer (QEQS)  
  
    -   Cas 3d : L’extraction en mode silencieux  
  
    -   Cas 3e : annuler l’extraction  
  
-   [Zone de test 4 : Archiver](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Cas 4 a : modification des éléments  
  
    -   Cas 4 b : ajout de fichiers  
  
    -   Cas c 4 : ajout de projets  
  
-   [Zone de test 5 : Modifier le contrôle de code source](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Cas 5 a : créer une liaison  
  
    -   Cas 5 b : supprimer la liaison  
  
    -   Cas 5c : relier  
  
-   [Zone de test 6 : Supprimer](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Zone de test 7 : Partager](../../extensibility/internals/test-area-7-share.md)  
  
-   [Zone de test 8 : Commutation de plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Cas 8 a : modification automatique  
  
    -   Cas 8 b : basée sur une Solution de modification  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)