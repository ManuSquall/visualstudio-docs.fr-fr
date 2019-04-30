---
title: Ensemble de règles des règles de globalisation pour le code managé
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28199eb9fa09e2096939ffa8e678eb9812a61b1f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816398"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles de globalisation pour le code managé
Vous pouvez utiliser la règle des règles de globalisation Microsoft à vous concentrer sur les problèmes qui peuvent empêcher des données dans votre application de s’afficher correctement dans différentes langues, paramètres régionaux et cultures. Vous devez inclure cet ensemble de règles si votre application est localisée, les globalisées, ou les deux.

|Règle|Description|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Spécifier MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Éviter les accélérateurs en double|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Ne pas coder en dur les chaînes spécifiques aux paramètres régionaux|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Ne pas passer de littéraux en paramètres localisés|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Spécifier CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Spécifier IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Définir les paramètres régionaux pour les types de données|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Spécifier StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normaliser les chaînes en majuscules|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Utiliser StringComparison avec la valeur Ordinal|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Spécifiez le marshaling pour les arguments de chaîne P/Invoke|