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
ms.openlocfilehash: 17bc9462af55ec9621654bd39cd65a2091f3f73f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740421"
---
# <a name="vscodewindowmanager-object"></a>Objet VSCodeWindowManager

Le service de langage implémente le gestionnaire de fenêtre de code et est chargé de gérer les ornements (par exemple, la barre de liste déroulante). Pour plus d’informations, consultez [Personnalisation des fenêtres de code à l’aide de l’API héritée](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

Le tableau suivant répertorie les interfaces de l' `VSCodeWindowManager` objet.

|Interface|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permet d’ajouter ou de supprimer des ornements (tels que des barres déroulantes) dans une fenêtre de code.|
