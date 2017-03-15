---
title: "CA1406&#160;: &#201;viter les arguments Int64 pour les clients Visual Basic&#160;6 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
helpviewer_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1406&#160;: &#201;viter les arguments Int64 pour les clients Visual Basic&#160;6
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type marqué spécifiquement comme étant visible dans COM \(Component Object Model\) déclare un membre qui accepte un argument <xref:System.Int64?displayProperty=fullName>.  
  
## Description de la règle  
 Les clients COM Visual Basic 6 ne peuvent pas accéder aux entiers de 64 bits.  
  
 Par défaut, les éléments suivants sont visibles par le modèle COM : assemblys, types publics, membres d'instances publics dans des types publics, et tous les membres de types valeur publics.  Toutefois, pour limiter les faux positifs, cette règle requiert que la visibilité COM du type soit déclarée explicitement ; l'assembly contenant doit être marqué avec <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ayant la valeur `false` et le type doit être marqué avec <xref:System.Runtime.InteropServices.ComVisibleAttribute> ayant la valeur `true`.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle pour un paramètre dont la valeur peut toujours être exprimée comme un intégral de 32 bits, remplacez le type de paramètre par <xref:System.Int32?displayProperty=fullName>.  Si la valeur du paramètre peut être plus grande que la valeur pouvant être exprimée comme un intégral de 32 bits, remplacez le type de paramètre par <xref:System.Decimal?displayProperty=fullName>.  Notez que <xref:System.Single?displayProperty=fullName> et <xref:System.Double?displayProperty=fullName> perdent en précision dans les plages supérieures du type de données <xref:System.Int64>.  Si le membre ne doit pas être visible dans COM, marquez\-le avec <xref:System.Runtime.InteropServices.ComVisibleAttribute> qui a la valeur `false`.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle s'il est certain que les clients COM Visual Basic 6 n'accèdent pas au type.  
  
## Exemple  
 L'exemple suivant présente un type qui enfreint la règle.  
  
 [!code-cs[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## Règles connexes  
 [CA1413 : Éviter les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407 : Éviter les membres statiques dans les types visibles par COM](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017 : Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Voir aussi  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long Data Type](/dotnet/visual-basic/language-reference/data-types/long-data-type)