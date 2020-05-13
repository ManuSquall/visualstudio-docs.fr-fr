---
title: Application des paramètres à travers plusieurs connexions de projets (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcaed0f7f2380dd36bcbffd776839025fe9efa16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710061"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Application des paramètres entre plusieurs connexions de projet
Un plug-in de contrôle source intégré à l’aide de la version API 1.2 de contrôle source peut utiliser une opération de lot pour exécuter la même opération de contrôle source sur plusieurs projets ou plusieurs contextes de connexion. Les lots peuvent être utilisés pour éliminer les boîtes de dialogue redondantes par projet de l’expérience utilisateur.

 Si un utilisateur sélectionne plusieurs éléments appartenant à plus d’une connexion dans un plug-in de contrôle source intégré à l’aide de la version API 1.1 de contrôle source (par exemple, deux projets Web sur différentes machines de partage de fichiers) et les vérifie, l’utilisateur voit la même boîte de dialogue à plusieurs reprises. Ce scénario se produit même si l’utilisateur clique sur la case à cocher **Apply to All** dans la case de dialogue, car l’IDE réinitialise son état pour chaque contexte de connexion.

## <a name="new-capability-flag"></a>Nouveau drapeau de capacité
 La `SccBeginBatch` fonction `SCC_CAP_BATCH` définit le drapeau pour indiquer qu’une opération de lot est en cours.

## <a name="new-functions"></a>Nouvelles fonctions
Les nouvelles fonctions suivantes prennent en charge l’opération de lot :

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

La `SCCBeginBatch` fonction démarre un groupe d’opérations de contrôle des sources. La `SccEndBatch` fonction ferme le groupe. Les groupes ne peuvent pas être imbriqués.

## <a name="see-also"></a>Voir aussi
- [Nouveauté dans la version API 1.2 du contrôle source](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
