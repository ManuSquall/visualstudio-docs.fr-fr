---
title: Énumérateurs | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711852"
---
# <a name="enumerators"></a>Énumérateurs
Cette section répertorie les types de données d’énumérateur dans l’API de plug-in de contrôle de code source que le plug-in de contrôle de code source doit connaître.

## <a name="in-this-section"></a>Contenu de cette section
- [Code de commande](../extensibility/command-code-enumerator.md) Énumère les options pour les fonctions [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et [SccPopulateList](../extensibility/sccpopulatelist-function.md) .

- [Message](../extensibility/message-enumerator.md) Énumère les indicateurs utilisés pour le rappel d’impression, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Code d’État du fichier](../extensibility/file-status-code-enumerator.md) Contient des valeurs constantes nommées qui spécifient l’état d’un fichier sous contrôle de code source.

- [Code d’État du répertoire](../extensibility/directory-status-code-enumerator.md) Contient des valeurs constantes nommées qui spécifient l’état d’un répertoire sous contrôle de code source.

## <a name="related-sections"></a>Sections connexes
- [Créer un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md) Définit le kit de développement logiciel (SDK) du plug-in de contrôle de code source et décrit les ressources incluses.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Invite l’utilisateur à fournir des options avancées pour la commande donnée.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Examine la liste des fichiers pour connaître leur état actuel. En outre, utilise la `pfnPopulate` fonction pour notifier l’appelant lorsqu’un fichier ne correspond pas aux critères de `nCommand` .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Décrit la fonction de rappel utilisée par [SccOpenProject](../extensibility/sccopenproject-function.md) pour afficher les messages du plug-in de contrôle de code source via l’IDE.

- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md) Fournit une liste complète de tous les éléments de l’API de plug-in de contrôle de code source.
