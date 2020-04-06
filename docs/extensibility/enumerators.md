---
title: Enumérateurs Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee48d064612e5519d5ad7e5eaf04de6c5a697837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711852"
---
# <a name="enumerators"></a>Énumérateurs
Cette section répertorie les types de données d’enumérateur dans l’API plug-in de contrôle source que le plug-in de contrôle source doit connaître.

## <a name="in-this-section"></a>Contenu de cette section
- [Code de commande](../extensibility/command-code-enumerator.md) Énumère les options pour les [fonctions SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

- [Message](../extensibility/message-enumerator.md) Énumére les drapeaux utilisés pour le rappel d’impression, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Code d’état du fichier](../extensibility/file-status-code-enumerator.md) Contient des valeurs constantes nommées qui spécifient l’état d’un fichier sous contrôle source.

- [Code d’état de l’annuaire](../extensibility/directory-status-code-enumerator.md) Contient des valeurs constantes nommées qui spécifient l’état d’un répertoire sous contrôle source.

## <a name="related-sections"></a>Sections connexes
- [Créer un plug-in de contrôle source](../extensibility/internals/creating-a-source-control-plug-in.md) Définit le SDK de contrôle source et décrit les ressources incluses.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Invite l’utilisateur à rechercher des options avancées pour la commande donnée.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Examine la liste des fichiers pour leur état actuel. En outre, `pfnPopulate` utilise la fonction pour informer l’appelant quand un `nCommand`fichier ne correspond pas aux critères pour le .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Décrit la fonction de rappel utilisée par [SccOpenProject](../extensibility/sccopenproject-function.md) pour afficher les messages du plug-in de contrôle source par l’intermédiaire de l’IDE.

- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md) Fournit une liste complète de tous les éléments de l’API rechargeable de contrôle source.
