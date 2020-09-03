---
title: Informations de référence sur les API non managées (développement Office dans Visual Studio)
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
ms.openlocfilehash: 4c1616d24ae9b2c072df4e5708eb98e86611a83d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540983"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Informations de référence sur les API non managées (développement Office dans Visual Studio)

À compter du système 2007 Microsoft Office, les applications Office utilisent l’interface d' [interface IManagedAddin](../vsto/imanagedaddin-interface.md) pour appeler un composant de chargeur de complément VSTO inclus avec [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Ce composant est utilisé pour aider les compléments VSTO gérés par le chargement. Vous pouvez créer votre propre composant de chargeur de complément VSTO en implémentant cette interface.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Contenu de cette section

[Interface IManagedAddin](../vsto/imanagedaddin-interface.md)

Interface COM que vous pouvez implémenter pour charger et décharger les compléments VSTO managés dans les applications Office.
