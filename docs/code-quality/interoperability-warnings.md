---
title: Avertissements sur la portabilité et l’interopérabilité
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- rules, portability
- interoperability rules
- rules, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8a456f4a24339b6cba5aeec2c9fe64ad3ee278b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808598"
---
# <a name="portability-and-interoperability-rules"></a>Règles de portabilité et d’interopérabilité

Les règles de portabilité prennent en charge la portabilité sur différentes plateformes. Les règles d’interopérabilité prennent en charge l’interaction avec les clients COM.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
| - | - |
| [Ca1401 : les P/Invoke ne doivent pas être visibles](../code-quality/ca1401.md) | Une méthode publique ou protégée dans un type public a l’attribut System.Runtime.InteropServices.DllImportAttribute (également implémenté par le mot clé Declare dans Visual Basic). De telles méthodes ne doivent pas être exposées. |
| [CA1416 : Valider la compatibilité de la plateforme](../code-quality/ca1416.md) | L’utilisation d’API dépendant de la plateforme sur un composant rend le code ne plus fonctionner sur toutes les plateformes. |
| [Ca1417 : ne pas utiliser `OutAttribute` sur les paramètres de chaîne pour les P/Invoke](../code-quality/ca1417.md) | Les paramètres de chaîne passés par valeur avec le `OutAttribute` peuvent déstabiliser le runtime si la chaîne est une chaîne internée. |
