---
title: 'CA2232 : marquer les points d’entrée Windows Forms avec STAThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 42bb554f8e57c036d41a89fdc2657a25ecc74e20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540281"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232 : Marquez les points d'entrée Windows Forms avec STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Un assembly fait référence <xref:System.Windows.Forms> à l’espace de noms, et son point d’entrée n’est pas marqué avec l' <xref:System.STAThreadAttribute?displayProperty=fullName> attribut.

## <a name="rule-description"></a>Description de la règle
 <xref:System.STAThreadAttribute> indique que le modèle de thread COM pour l’application est un thread cloisonné. Cet attribut doit être présent au point d'entrée de toute application qui utilise des Windows Forms ; s'il est omis, les composants Windows peuvent ne pas fonctionner correctement. Si l’attribut n’est pas présent, l’application utilise le modèle multithread cloisonné, qui n’est pas pris en charge pour les Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] les projets qui utilisent l’infrastructure d’application n’ont pas besoin de marquer la méthode **main** avec STAThread. Le [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilateur le fait automatiquement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez l' <xref:System.STAThreadAttribute> attribut au point d’entrée. Si l' <xref:System.MTAThreadAttribute?displayProperty=fullName> attribut est présent, supprimez-le.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si vous développez pour le .NET Compact Framework, pour lequel l' <xref:System.STAThreadAttribute> attribut est inutile et n’est pas pris en charge.

## <a name="example"></a>Exemple
 Les exemples suivants illustrent l’utilisation correcte de <xref:System.STAThreadAttribute> .

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
