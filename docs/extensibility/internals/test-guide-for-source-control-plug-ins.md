---
title: Guide d’essai pour les plug-ins de contrôle des sources (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6b3f8e76e977472a3459697a650b32dae657c22
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704377"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guide de test pour les plug-ins de contrôle de code source
Cette section fournit des conseils pour tester [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]votre plug-in de contrôle source avec . Un aperçu complet des zones d’essai les plus courantes, ainsi que certains des domaines les plus complexes qui peuvent être problématiques, sont fournis. Cette vue d’ensemble n’est pas censée être une liste exhaustive des cas de test.

> [!NOTE]
> Certaines corrections de bogues [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et des améliorations à la dernière IDE peut découvrir des problèmes avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]les plug-ins de contrôle source existants qui n’ont pas été rencontrés auparavant lors de l’utilisation des versions précédentes de . Il est fortement recommandé que vous testiez votre plug-in de contrôle source existant pour les zones énumérées dans cette [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]section, même si aucun changement n’a été apporté au plug-in depuis la version précédente de .

## <a name="common-preparation"></a>Préparation commune
 Une machine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avec et le plug-in de commande de source cible installé, est exigée. Une deuxième machine également configurée peut être utilisée pour certains des tests Open from Source Control.

## <a name="definition-of-terms"></a>Définition des termes
 Aux fins de ce guide de test, utilisez les définitions de terme suivantes :

 Projet client Tout type [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de projet disponible dans [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]celui [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]prend [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]en charge l’intégration de contrôle des sources (par exemple, , , ou ).

 Projet Web Il existe quatre types de projets Web : Système de fichiers, LOCAL IIS, sites distants et FTP.

- Les projets du système de fichiers sont créés sur une voie locale, mais ils n’exigent pas l’installation des Services d’information Sur Internet (IIS) car ils sont accessibles en interne via une voie unC, et peuvent être placés sous contrôle source de l’intérieur de l’IDE, tout comme les projets clients.

- Les projets locaux d’IIS fonctionnent avec l’IIS qui est installé sur la même machine et sont accessibles avec une URL pointant vers la machine locale.

- Les projets Sites Distant sont également créés dans le cadre d’un service IIS, mais ils sont placés sous contrôle source sur la machine serveur IIS et non de l’intérieur de l’IDE. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

- Les projets FTP sont accessibles via un serveur FTP distant, mais ils ne peuvent pas être placés sous contrôle source.

  Enrôlement Un autre terme pour la solution ou le projet sous contrôle source.

  Version Store La base de données de contrôle source accessible via l’API rechargeable de contrôle source.

## <a name="test-areas-covered-in-this-section"></a>Zones d’essai couvertes dans cette section

- [Zone d’essai 1 : Ajouter à/ouvrir à partir du contrôle source](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Cas 1a : Ajouter la solution au contrôle des sources

  - Cas 1b : Solution ouverte à partir du contrôle des sources

  - Cas 1c : Ajouter la solution à partir du contrôle des sources

- [Zone de test 2 : Obtenir à partir du contrôle de code source](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Zone d’essai 3: Départ/Annuler](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Cas 3: Check Out/Undo Checkout

  - Cas 3a: Check Out

  - Cas 3b: Caisse déconnectée

  - Cas 3c: Requête Edit/Requête Save (QEQS)

  - Cas 3d: Silent Checkout

  - Cas 3e: Annuler la caisse

- [Zone de test 4 : Archiver](../../extensibility/internals/test-area-4-check-in.md)

  - Cas 4a : Articles modifiés

  - Cas 4b : Ajout de fichiers

  - Cas 4c : Ajout de projets

- [Zone de test 5 : Modifier le contrôle de code source](../../extensibility/internals/test-area-5-change-source-control.md)

  - Cas 5a: Bind

  - Cas 5b: Unbind

  - Cas 5c: Rebind

- [Zone de test 6 : Supprimer](../../extensibility/internals/test-area-6-delete.md)

- [Zone de test 7 : Partager](../../extensibility/internals/test-area-7-share.md)

- [Zone de test 8 : Commutation de plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Cas 8a: Changement automatique

  - Cas 8b : Changement basé sur la solution

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)
