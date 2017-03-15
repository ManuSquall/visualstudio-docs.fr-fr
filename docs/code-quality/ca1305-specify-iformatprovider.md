---
title: "CA1305&#160;: Sp&#233;cifier IFormatProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyIFormatProvider"
  - "CA1305"
helpviewer_keywords: 
  - "CA1305"
  - "SpecifyIFormatProvider"
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1305&#160;: Sp&#233;cifier IFormatProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode ou un constructeur appelle un ou plusieurs membres présentant des surcharges qui acceptent un paramètre <xref:System.IFormatProvider?displayProperty=fullName>, et la méthode ou le constructeur n'appelle pas la surcharge qui accepte le paramètre <xref:System.IFormatProvider>.  Cette règle ignore les appels aux méthodes du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] documentées comme ignorant le paramètre <xref:System.IFormatProvider> ainsi qu'aux méthodes suivantes :  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## Description de la règle  
 Lorsqu'un objet <xref:System.Globalization.CultureInfo?displayProperty=fullName> ou <xref:System.IFormatProvider> n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté dans toutes les configurations régionales.  De plus, les membres du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] choisissent la culture par défaut et la mise en forme en fonction d'hypothèses qui peuvent se révéler incorrectes pour votre code.  Pour garantir le fonctionnement du code attendu dans vos scénarios, vous devez fournir des informations spécifiques à la culture, conformément aux indications suivantes :  
  
-   Si la valeur est présentée à l'utilisateur, utilisez la culture actuelle.  Consultez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Si la valeur est stockée et fait l'objet d'accès par voie logicielle, c'est\-à\-dire si elle est rendue persistante dans un fichier ou une base de données, utilisez la culture indifférente.  Consultez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Si vous ne connaissez pas la destination de la valeur, faites en sorte que le consommateur ou le fournisseur de données spécifie la culture.  
  
 Remarquez que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> est utilisé uniquement pour récupérer des ressources localisées à l'aide d'une instance de la classe <xref:System.Resources.ResourceManager?displayProperty=fullName>.  
  
 Même si le comportement par défaut du membre surchargé est adapté à vos besoins, mieux vaut appeler explicitement la surcharge spécifique à la culture afin que votre code soit automatiquement documenté et plus facile à gérer.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, utilisez la surcharge qui accepte un <xref:System.Globalization.CultureInfo> ou un <xref:System.IFormatProvider>, puis spécifiez l'argument d'après les indications répertoriées précédemment.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle lorsqu'il est certain que la culture\/le fournisseur de format par défaut constitue le choix correct et lorsque la facilité de maintenance du code ne constitue pas une priorité de développement importante.  
  
## Exemple  
 Dans l'exemple suivant, `BadMethod` provoque deux violations de cette règle.  `GoodMethod` corrige la première violation en passant la culture dite indifférente à <xref:System.String.Compare%2A>, et corrige la deuxième violation en passant la culture actuelle à <xref:System.String.ToLower%2A> parce que `string3` est visible par l'utilisateur.  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## Exemple  
 L'exemple suivant illustre l'effet de la culture actuelle sur le <xref:System.IFormatProvider> par défaut sélectionné par le type <xref:System.DateTime>.  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **6\/4\/1900 12:15:12 PM 06\/04\/1900 12:15:12**   
## Règles connexes  
 [CA1304 : Spécifier CultureInfo](../Topic/CA1304:%20Specify%20CultureInfo.md)  
  
## Voir aussi  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/fr-fr/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)