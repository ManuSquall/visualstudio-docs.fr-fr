---
title: Interface IActiveScriptSiteDebugEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 605505d101611dfe39835671b042852eab5ca9cb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992386"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx (interface)

Implémentez cette interface avec le `IActiveScriptSiteDebug` interface si vous écrivez un hôte qui doit recevoir une notification d’une erreur d’exécution dans une application et éventuellement l’attacher à l’application pour le débogage. Le Gestionnaire de débogage de processus fournit une notification via `IActiveScriptDebug` si un juste-à-temps débogueur de script se trouve sur l’ordinateur. Si le débogueur de script aucun juste-à-temps est trouvé, PDM fournit une notification via `IActiveScriptDebugEx` à la place.

Pour obtenir une notification d’une erreur d’exécution, votre hôte doit traiter `ActiveScriptSiteDebug::OnScriptErrorDebug`. Selon une action de l’utilisateur, vous pouvez alors décider pour attacher le débogueur interne et un retour, ou pour retourner le démarrage du débogueur dans le OnScriptErrorDebug `pfEnterDebugger` paramètre.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable

|Méthode|Description|
|------------|-----------------|
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informe l’hôte sur une erreur d’exécution de script lorsque le processus de débogage Manager ne trouve pas un débogueur juste à temps externe.|