---
title: Ensemble de règles des règles de globalisation pour le code managé
ms.date: 11/04/2016
description: En savoir plus sur l’ensemble de règles des règles de globalisation dans Visual Studio, qui se concentre sur les problèmes liés aux langues, aux paramètres régionaux et aux cultures. Consultez Description de la règle.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: fdf816b978aac5d22b1750eeabe3737f1eb64085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867930"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles de globalisation pour le code managé

Utilisez l’ensemble de règles des règles de globalisation Microsoft pour vous concentrer sur les problèmes susceptibles d’empêcher l’affichage correct des données de votre application dans différentes langues, paramètres régionaux et cultures. Vous devez inclure cet ensemble de règles si votre application est localisée, globalisée ou les deux.

|Règle|Description|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Ne pas passer de littéraux en paramètres localisés|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|Spécifier CultureInfo|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|Spécifier IFormatProvider|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|Spécifier StringComparison pour plus de clarté|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Normaliser les chaînes en majuscules|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|Utiliser StringComparison avec la valeur Ordinal|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|Spécifier StringComparison pour l’exactitude|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Spécifiez le marshaling pour les arguments de chaîne P/Invoke|
