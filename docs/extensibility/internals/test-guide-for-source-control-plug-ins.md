---
title: Guide de test pour les plug-ins de contrôle de code source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51595708bf30472fd001bde394c7d8c80e39ad45
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722400"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guide de test pour les plug-ins de contrôle de code source
Cette section fournit des conseils sur le test de votre plug-in de contrôle de code source avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Une vue d’ensemble complète des zones de test les plus courantes, ainsi que certaines des zones les plus compliquées qui peuvent être problématiques sont fournies. Cette vue d’ensemble n’est pas censée être une liste exhaustive des cas de test.

> [!NOTE]
> Certains correctifs de bogues et les améliorations apportées à la dernière [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE peuvent découvrir des problèmes avec des plug-ins de contrôle de code source existants qui n’ont pas été rencontrés précédemment lors de l’utilisation de versions antérieures de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Il est fortement recommandé de tester votre plug-in de contrôle de code source existant pour les zones énumérées dans cette section, même si aucune modification n’a été apportée au plug-in depuis la version précédente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="common-preparation"></a>Préparation courante
 Un ordinateur avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et le plug-in de contrôle de code source cible doit être installé. Un deuxième ordinateur configuré de la même façon peut être utilisé pour certaines des tests ouverts à partir du contrôle de code source.

## <a name="definition-of-terms"></a>Définition des termes
 Pour les besoins de ce guide de test, utilisez les définitions de terme suivantes :

 Projet client tout type de projet disponible dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qui prend en charge l’intégration du contrôle de code source (par exemple, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 Projet Web il existe quatre types de projets Web : système de fichiers, IIS local, sites distants et FTP.

- Les projets de système de fichiers sont créés sur un chemin d’accès local, mais ils ne nécessitent pas l’installation du Internet Information Services (IIS), car ils sont accessibles en interne via un chemin d’accès UNC et peuvent être placés sous contrôle de code source à partir de l’IDE, de la même façon que les projets clients.

- Les projets IIS locaux fonctionnent avec IIS qui est installé sur le même ordinateur et sont accessibles à l’aide d’une URL pointant vers l’ordinateur local.

- Les projets de sites distants sont également créés sous un service IIS, mais ils sont placés sous contrôle de code source sur l’ordinateur serveur IIS et non à l’intérieur de l’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Les projets FTP sont accessibles via un serveur FTP distant, mais ils ne peuvent pas être placés sous contrôle de code source.

  Inscrit un autre terme pour la solution ou le projet sous contrôle de code source.

  Banque des versions : base de données de contrôle de code source accessible via l’API de plug-in de contrôle de code source.

## <a name="test-areas-covered-in-this-section"></a>Zones de test couvertes dans cette section

- [Zone de test 1 : Ajouter à/Ouvrir à partir du contrôle de code source](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Cas 1a : ajouter la solution au contrôle de code source

  - Cas 1b : ouvrir la solution à partir du contrôle de code source

  - Cas 1C : ajouter la solution à partir du contrôle de code source

- [Zone de test 2 : Obtenir à partir du contrôle de code source](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Zone de test 3 : Extraire/Annuler l’extraction](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Cas 3 : extraire/annuler l’extraction

  - Cas 3a : extraire

  - Cas 3b : extraction déconnectée

  - Cas 3C : modification de requête/requête d’enregistrement (provenant QEQS)

  - Cas 3D : extraction silencieuse

  - Cas 3e : annuler l’extraction

- [Zone de test 4 : Archiver](../../extensibility/internals/test-area-4-check-in.md)

  - Cas 4a : éléments modifiés

  - Cas 4b : ajout de fichiers

  - Cas 4C : ajout de projets

- [Zone de test 5 : Modifier le contrôle de code source](../../extensibility/internals/test-area-5-change-source-control.md)

  - Cas 5A : lier

  - Cas 5B : Unbind

  - Cas 5C : relier

- [Zone de test 6 : Supprimer](../../extensibility/internals/test-area-6-delete.md)

- [Zone de test 7 : Partager](../../extensibility/internals/test-area-7-share.md)

- [Zone de test 8 : Commutation de plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Cas 8A : modification automatique

  - Cas 8B : modification basée sur la solution

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)
