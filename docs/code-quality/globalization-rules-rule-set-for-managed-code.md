---
title: Ensemble de règles de règles de globalisation pour le code managé | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 54e1df6f8c49112747ccd7254f01a57d33dccf0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles de globalisation pour le code managé
Vous pouvez utiliser la règle des règles de globalisation Microsoft à vous concentrer sur les problèmes qui peuvent empêcher les données dans votre application de s’afficher correctement dans différentes langues, paramètres régionaux et cultures. Vous devez inclure cet ensemble de règles si votre application est localisée, les globalisées, ou les deux.  
  
|Règle|Description|  
|----------|-----------------|  
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Spécifier MessageBoxOptions|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Éviter les accélérateurs en double|  
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Ne pas coder en dur les chaînes spécifiques aux paramètres régionaux|  
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Ne pas transmettre des littéraux en tant que paramètres localisés|  
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Spécifier CultureInfo|  
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Spécifier IFormatProvider|  
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Définir les paramètres régionaux pour les types de données|  
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Spécifier StringComparison|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normaliser les chaînes en majuscules|  
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Utiliser StringComparison avec la valeur ordinal|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Spécifiez le marshaling pour les arguments de chaîne P/Invoke|