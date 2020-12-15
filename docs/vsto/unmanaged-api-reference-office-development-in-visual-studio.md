---
title: Informations de référence sur les API non managées (développement Office dans Visual Studio)
description: La référence d’API non managée est utilisée pour aider les compléments VSTO gérés par le chargement. Vous pouvez également créer votre propre composant de chargeur de complément VSTO en implémentant cette interface.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9dbb64b54d9b0dd9a244d9a614fbce211d1edfc5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522685"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Informations de référence sur les API non managées (développement Office dans Visual Studio)

À compter du système 2007 Microsoft Office, les applications Office utilisent l’interface d' [interface IManagedAddin](../vsto/imanagedaddin-interface.md) pour appeler un composant de chargeur de complément VSTO inclus avec [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Ce composant est utilisé pour aider les compléments VSTO gérés par le chargement. Vous pouvez créer votre propre composant de chargeur de complément VSTO en implémentant cette interface.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Dans cette section

[Interface IManagedAddin](../vsto/imanagedaddin-interface.md)

Interface COM que vous pouvez implémenter pour charger et décharger les compléments VSTO managés dans les applications Office.
