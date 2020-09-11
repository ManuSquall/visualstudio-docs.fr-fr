---
title: Objet VSCodeWindowManager | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fea97c8784402c55947c108f42f2f3153f322d9c
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012384"
---
# <a name="vscodewindowmanager-object"></a>Objet VSCodeWindowManager

Le service de langage implémente le gestionnaire de fenêtre de code et est chargé de gérer les ornements (par exemple, la barre de liste déroulante). Pour plus d’informations, consultez [Personnalisation des fenêtres de code à l’aide de l’API héritée](../vs-2015/extensibility/customizing-code-windows-by-using-the-legacy-api.md?view=vs-2015).

Le tableau suivant répertorie les interfaces de l' `VSCodeWindowManager` objet.

|Interface|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permet d’ajouter ou de supprimer des ornements (tels que des barres déroulantes) dans une fenêtre de code.|