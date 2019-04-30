---
title: "CA2232 : Marquez les points d'entrée Windows Forms avec STAThread"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1bea8ee43c90c0e6559846bad00b61ec434ec46f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541807"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232 : Marquez les points d'entrée Windows Forms avec STAThread

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
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] les projets qui utilisent l’infrastructure d’Application n’ont pas marquer le **Main** méthode avec STAThread. Le [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilateur effectue automatiquement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez le <xref:System.STAThreadAttribute> attribut au point d’entrée. Si le <xref:System.MTAThreadAttribute?displayProperty=fullName> attribut n’est présent, supprimez-le.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si vous développez pour le .NET Compact Framework pour lequel le <xref:System.STAThreadAttribute> attribut n’est pas nécessaire et non pris en charge.

## <a name="example"></a>Exemple
 Les exemples suivants illustrent l’utilisation correcte de <xref:System.STAThreadAttribute>:

 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]