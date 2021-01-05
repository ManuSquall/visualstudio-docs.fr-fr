---
title: Objet VSCodeWindowManager | Microsoft Docs
description: En savoir plus sur l’objet VSCodeWindowManager, qui est responsable de la gestion des ornements, par exemple, la barre déroulante.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7a5c602a1cf46382e5a8b5c688501b2406e4a6d0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863998"
---
# <a name="vscodewindowmanager-object"></a>Objet VSCodeWindowManager

Le service de langage implémente le gestionnaire de fenêtre de code et est chargé de gérer les ornements (par exemple, la barre de liste déroulante). Pour plus d’informations, consultez [Personnalisation des fenêtres de code à l’aide de l’API héritée](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

Le tableau suivant répertorie les interfaces de l' `VSCodeWindowManager` objet.

|Interface|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permet d’ajouter ou de supprimer des ornements (tels que des barres déroulantes) dans une fenêtre de code.|