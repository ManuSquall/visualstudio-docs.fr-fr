---
title: Avertissements sur la portabilité et l’interopérabilité
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings, portability warnings
- portability warnings
- warnings, portability
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 306c2477e6e5f731ed6dbf20b2cf4d03d4556467
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509911"
---
# <a name="portability-and-interoperability-warnings"></a>Avertissements sur la portabilité et l’interopérabilité

Les avertissements de portabilité prennent en charge la portabilité sur différentes plateformes. Les avertissements d’interopérabilité prennent en charge l’interaction avec les clients COM.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
| - | - |
| [Ca1401 : les P/Invoke ne doivent pas être visibles](../code-quality/ca1401.md) | Une méthode publique ou protégée dans un type public a l’attribut System.Runtime.InteropServices.DllImportAttribute (également implémenté par le mot clé Declare dans Visual Basic). De telles méthodes ne doivent pas être exposées. |
| [Ca1417 : ne pas utiliser `OutAttribute` sur les paramètres de chaîne pour les P/Invoke](../code-quality/ca1417.md) | Les paramètres de chaîne passés par valeur avec le `OutAttribute` peuvent déstabiliser le runtime si la chaîne est une chaîne internée. |