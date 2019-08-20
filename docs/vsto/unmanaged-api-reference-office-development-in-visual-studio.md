---
title: Informations de référence sur les API non managées (développement Office dans Visual Studio)
ms.date: 08/14/2019
ms.topic: conceptual
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
ms.openlocfilehash: 00db78359154dbda600fb4b58103bc04e89d16b2
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551321"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Informations de référence sur les API non managées (développement Office dans Visual Studio)

À compter du système 2007 Microsoft Office, les applications Office utilisent l’interface d' [interface IManagedAddin](../vsto/imanagedaddin-interface.md) pour appeler un composant de chargeur de complément VSTO inclus avec [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ce composant est utilisé pour aider les compléments VSTO gérés par le chargement. Vous pouvez créer votre propre composant de chargeur de complément VSTO en implémentant cette interface.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Dans cette section

[Interface IManagedAddin](../vsto/imanagedaddin-interface.md)

Interface COM que vous pouvez implémenter pour charger et décharger les compléments VSTO managés dans les applications Office.
