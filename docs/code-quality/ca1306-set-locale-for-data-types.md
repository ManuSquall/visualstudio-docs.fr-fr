---
title: "CA1306&#160;: D&#233;finir les param&#232;tres r&#233;gionaux pour les types de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
helpviewer_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1306&#160;: D&#233;finir les param&#232;tres r&#233;gionaux pour les types de donn&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode ou constructeur a créé une ou plusieurs instances de <xref:System.Data.DataTable?displayProperty=fullName> ou <xref:System.Data.DataSet?displayProperty=fullName> et n'a pas défini explicitement la propriété de paramètres régionaux \(<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> ou <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>\).  
  
## Description de la règle  
 Les paramètres régionaux déterminent des éléments de présentation des données spécifiques à la culture, telles que la mise en forme utilisée pour les valeurs numériques, les symboles monétaires et l'ordre de tri.  Lorsque vous créez un <xref:System.Data.DataTable> ou un <xref:System.Data.DataSet>, vous devez définir les paramètres régionaux explicitement.  Par défaut, les paramètres régionaux de ces types sont la culture actuelle.  Pour les données stockées dans une base de données ou un fichier et partagées globalement, les paramètres régionaux devraient normalement avoir pour valeur la culture indifférente \(<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>\).  Lorsque les données sont partagées à l'échelle des différentes cultures, le recours à des paramètres régionaux par défaut peut entraîner une présentation ou une interprétation incorrecte des contenus du <xref:System.Data.DataTable> ou du <xref:System.Data.DataSet>.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, définissez explicitement les paramètres régionaux \(via la propriété locale\) pour le <xref:System.Data.DataTable> ou le <xref:System.Data.DataSet>.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle lorsque la bibliothèque ou l'application est destinée à une audience locale limitée, lorsque les données ne sont pas partagées, ou lorsque le paramétrage par défaut débouche sur le comportement désiré dans tous les scénarios pris en charge.  
  
## Exemple  
 L'exemple suivant crée deux instances de <xref:System.Data.DataTable>.  
  
 [!code-cs[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## Voir aussi  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>