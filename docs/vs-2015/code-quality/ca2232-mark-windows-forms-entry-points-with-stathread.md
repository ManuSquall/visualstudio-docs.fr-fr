---
title: 'CA2232 : Points d’entrée d’interrogation Windows Forms avec STAThread | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d486189b557c0c1146be68e6c0328cb49d5ed291
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953359"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232 : Marquez les points d'entrée Windows Forms avec STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Fait référence à un assembly la <xref:System.Windows.Forms> espace de noms et son point d’entrée n’est pas marqué avec le <xref:System.STAThreadAttribute?displayProperty=fullName> attribut.

## <a name="rule-description"></a>Description de la règle
 <xref:System.STAThreadAttribute> Indique que le modèle pour l’application de thread COM est à thread unique cloisonné. Cet attribut doit être présent au point d'entrée de toute application qui utilise des Windows Forms ; s'il est omis, les composants Windows peuvent ne pas fonctionner correctement. Si l’attribut n’est pas présent, l’application utilise le modèle de cloisonnement multithread, ce qui n’est pas pris en charge pour les Windows Forms.

> [!NOTE]
>  [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] les projets qui utilisent l’infrastructure d’Application n’ont pas marquer le **Main** méthode avec STAThread. Le [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilateur effectue automatiquement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez le <xref:System.STAThreadAttribute> attribut au point d’entrée. Si le <xref:System.MTAThreadAttribute?displayProperty=fullName> attribut n’est présent, supprimez-le.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si vous développez pour le .NET Compact Framework pour lequel le <xref:System.STAThreadAttribute> attribut n’est pas nécessaire et non pris en charge.

## <a name="example"></a>Exemple
 Les exemples suivants illustrent l’utilisation correcte de <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
