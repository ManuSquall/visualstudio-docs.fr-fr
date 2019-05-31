---
title: Énumérateurs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d3a0876dfd3a9d7b9cc86b18f6e9a6ba3b780d3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334509"
---
# <a name="enumerators"></a>Énumérateurs
Cette section répertorie les types de données d’énumérateur dans l’API de plug-in de contrôle de Source que le plug-in de contrôle de code source doit connaître.

## <a name="in-this-section"></a>Dans cette section
- [Code de commande](../extensibility/command-code-enumerator.md) énumère les options pour le [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et [SccPopulateList](../extensibility/sccpopulatelist-function.md) fonctions.

- [Message](../extensibility/message-enumerator.md) énumère les indicateurs utilisés pour le rappel d’impression, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Fichier de code d’état](../extensibility/file-status-code-enumerator.md) Contains nommé des valeurs constantes qui spécifient l’état d’un fichier sous contrôle de code source.

- [Code d’état Directory](../extensibility/directory-status-code-enumerator.md) Contains nommé des valeurs constantes qui spécifient l’état d’un répertoire sous contrôle de code source.

## <a name="related-sections"></a>Rubriques connexes
- [Créer un contrôle de source de plug-in](../extensibility/internals/creating-a-source-control-plug-in.md) définit le SDK de plug-in de contrôle de Source et décrit les ressources incluses.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) invite l’utilisateur pour les options avancées pour la commande donnée.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) examine la liste des fichiers pour leur état actuel. En outre, utilise le `pfnPopulate` fonction permettant de notifier l’appelant quand un fichier ne correspond pas aux critères pour le `nCommand`.

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) décrit la fonction de rappel qui est utilisée par [SccOpenProject](../extensibility/sccopenproject-function.md) pour afficher les messages de contrôle de source de plug-in via l’IDE.

- [Plug-ins de contrôle de source](../extensibility/source-control-plug-ins.md) fournit une liste complète de tous les éléments dans l’API de plug-in de contrôle de Source.