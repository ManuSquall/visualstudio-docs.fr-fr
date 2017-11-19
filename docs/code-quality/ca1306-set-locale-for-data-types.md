---
title: "CA1306 : Définir les paramètres régionaux pour les types de données | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2a8760aa983cdd798e5ea46fa4161375f0eab7fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306 : Définir les paramètres régionaux pour les types de données
|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode ou un constructeur créé une ou plusieurs <xref:System.Data.DataTable?displayProperty=fullName> ou <xref:System.Data.DataSet?displayProperty=fullName> instances et définissait pas explicitement la propriété de paramètres régionaux (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> ou <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).  
  
## <a name="rule-description"></a>Description de la règle  
 Les paramètres régionaux déterminent des éléments de présentation spécifiques à la culture des données, telles que la mise en forme utilisée pour les valeurs numériques, les symboles monétaires et ordre de tri. Lorsque vous créez un <xref:System.Data.DataTable> ou <xref:System.Data.DataSet>, vous devez définir les paramètres régionaux explicitement. Par défaut, les paramètres régionaux pour ces types sont la culture actuelle. Pour les données qui sont stockées dans un fichier ou une base de données et sont partagées globalement, les paramètres régionaux doivent normalement être définis pour la culture dite indifférente (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Lorsque les données sont partagées entre les cultures, à l’aide des paramètres régionaux par défaut peut entraîner le contenu de la <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> présentation ou incorrectement interprétés.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, définir explicitement les paramètres régionaux pour le <xref:System.Data.DataTable> ou <xref:System.Data.DataSet>.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle lorsque la bibliothèque ou l’application est destiné à une audience locale limitée, les données ne sont pas partagées, ou le paramètre par défaut génère le comportement souhaité dans tous les scénarios pris en charge.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée deux <xref:System.Data.DataTable> instances.  
  
 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>