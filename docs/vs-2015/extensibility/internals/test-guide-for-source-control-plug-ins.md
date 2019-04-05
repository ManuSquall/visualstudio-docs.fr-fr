---
title: Guide de test de Plug-ins de contrôle de code Source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 194c1e926ead79d5db05e530e2345aa4c722aa21
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950263"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guide de test pour les plug-ins de contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette section fournit des conseils pour tester votre contrôle de source de plug-in avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Une vue d’ensemble complète des zones de tests les plus courantes, ainsi que certains domaines plus complexes qui peuvent s’avérer problématiques est fourni. Cette vue d’ensemble n’est pas censée être une liste exhaustive des cas de test.  
  
> [!NOTE]
>  Certains correctifs de bogues et les améliorations apportées à la dernière version [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE peut découvrir des problèmes avec la source contrôle plug-ins existants qui étaient précédemment pas lors de l’utilisation des versions précédentes de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Il est fortement recommandé de tester votre contrôle de code source existant plug-in pour les zones énumérés dans cette section, même si aucune modification n’ont été apportées pour le plug-in depuis la version précédente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="common-preparation"></a>Préparation courantes  
 Un ordinateur avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et le contrôle de code source cible plug-in installé, est requis. Un deuxième ordinateur configuré de la même façon utilisable pour une partie de l’ouvrir à partir de tests de contrôle de code Source.  
  
## <a name="definition-of-terms"></a>Définition des termes  
 Pour les besoins de ce guide de test, utilisez les définitions des termes suivants :  
  
 Projet client  
 Un projet de type disponible dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] qui prend en charge l’intégration du contrôle de code source (par exemple, [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], ou [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]).  
  
 projet Web  
 Il existe quatre types de projets Web : Système de fichiers, serveur IIS Local, Sites distants et FTP.  
  
- Projets de système de fichiers sont créés sur un chemin d’accès local, mais ils ne nécessitent pas d’Internet Information Services (IIS) pour être installé car ils sont accessibles en interne via un chemin d’accès UNC et peuvent être placées sous contrôle de code source à partir de l’IDE, comme les projets clients.  
  
- Les projets IIS locaux fonctionnent avec IIS, qui est installé sur le même ordinateur et sont accessibles avec une URL pointant vers l’ordinateur local.  
  
- Les projets de Sites à distance sont également créés sous les Services IIS, mais ils sont placés sous contrôle de code source sur l’ordinateur du serveur IIS et non à partir à l’intérieur de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
- Projets FTP sont accessibles via un serveur FTP distant, mais ils ne peuvent pas être placés sous contrôle de code source.  
  
  Inscription  
  Un autre terme pour la solution ou un projet sous contrôle de code source.  
  
  Version Store  
  La base de données de contrôle de source est accessible via l’API de plug-in de contrôle de Source.  
  
## <a name="test-areas-covered-in-this-section"></a>Cette Section traités des zones de test  
  
-   [Zone de test 1 : Ajouter / Ouvrir à partir du contrôle de code Source](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Cas 1 : Ajoutez la Solution au contrôle de code Source  
  
    -   1 b cas : Ouvrir une Solution à partir du contrôle de code Source  
  
    -   Cas 1c : Ajouter la Solution à partir du contrôle de code Source  
  
-   [Zone de test 2 : Obtenir à partir du contrôle de code Source](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Zone de test 3 : Découvrez / annuler l’extraction](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Cas 3 : Découvrez / annuler l’extraction  
  
    -   Cas 3 : Extraire  
  
    -   3 b de cas : Extraction déconnectée  
  
    -   Cas 3c : Modifier/la requête d’enregistrement (QEQS)  
  
    -   Cas 3d : Extraction en mode silencieux  
  
    -   3e cas : Annuler l’extraction  
  
-   [Zone de test 4 : Date d'arrivée](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   4 a case : Éléments modifiés  
  
    -   4 b de cas : Ajout de fichiers  
  
    -   Cas 4c : Ajout de projets  
  
-   [Zone de test 5 : Modifier le contrôle de code Source](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   5 a case : Lier  
  
    -   5 b de cas : Annuler la liaison  
  
    -   Cas 5c : reliaison  
  
-   [Zone de test 6 : Delete](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Zone de test 7 : Partager](../../extensibility/internals/test-area-7-share.md)  
  
-   [Zone de test 8 : Commutation de plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   8 a case : Modification automatique  
  
    -   8 b de cas : Modification sur les solutions  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)
