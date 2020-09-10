---
title: Appliquer des paramètres sur plusieurs connexions de projet
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
ms.openlocfilehash: 5c88a5140bf72f6801d4c7a92ebd910f410aabfb
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741525"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Application de paramètres sur plusieurs connexions de projet
Un plug-in de contrôle de code source créé à l’aide de la version 1,2 de l’API de plug-in de contrôle de code source peut utiliser une opération de traitement par lot pour exécuter la même opération de contrôle de code source sur plusieurs projets ou plusieurs contextes de connexion. Les lots peuvent être utilisés pour éliminer les boîtes de dialogue redondantes et par projet de l’expérience utilisateur.

 Si un utilisateur sélectionne plusieurs éléments appartenant à plusieurs connexions dans un plug-in de contrôle de code source créé à l’aide de la version 1,1 de l’API de plug-in de contrôle de code source (par exemple, deux projets Web sur différents ordinateurs de partage de fichiers) et les extrait, l’utilisateur voit la même boîte de dialogue de façon répétée. Ce scénario se produit même si l’utilisateur clique sur la case à cocher **appliquer à tous** dans la boîte de dialogue, car l’environnement de développement intégré (IDE) réinitialise son état pour chaque contexte de connexion.

## <a name="new-capability-flag"></a>Nouvel indicateur de fonctionnalité
 La `SccBeginBatch` fonction définit l' `SCC_CAP_BATCH` indicateur pour indiquer qu’une opération de traitement par lot est en cours.

## <a name="new-functions"></a>Nouvelles fonctions
Les nouvelles fonctions suivantes prennent en charge l’opération de traitement par lots :

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

La `SCCBeginBatch` fonction démarre un groupe d’opérations de contrôle de code source. La `SccEndBatch` fonction ferme le groupe. Les groupes ne peuvent pas être imbriqués.

## <a name="see-also"></a>Voir aussi
- [Nouveautés de l’API de plug-in de contrôle de code source version 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
