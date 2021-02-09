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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e353070c780f69ea05c1c67986f7a40f34d0659c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925843"
---
# <a name="vscodewindowmanager-object"></a>Objet VSCodeWindowManager

Le service de langage implémente le gestionnaire de fenêtre de code et est chargé de gérer les ornements (par exemple, la barre de liste déroulante). Pour plus d’informations, consultez [Personnalisation des fenêtres de code à l’aide de l’API héritée](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

Le tableau suivant répertorie les interfaces de l' `VSCodeWindowManager` objet.

|Interface|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permet d’ajouter ou de supprimer des ornements (tels que des barres déroulantes) dans une fenêtre de code.|