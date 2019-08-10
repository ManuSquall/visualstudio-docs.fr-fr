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
ms.openlocfilehash: dd3f5b76015a3a54ee085b5cc2dd532920ff0795
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920177"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232 : Marquez les points d'entrée Windows Forms avec STAThread

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Catégorie|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un assembly fait <xref:System.Windows.Forms> référence à l’espace de noms, et son point d' <xref:System.STAThreadAttribute?displayProperty=fullName> entrée n’est pas marqué avec l’attribut.

## <a name="rule-description"></a>Description de la règle
 <xref:System.STAThreadAttribute>indique que le modèle de thread COM pour l’application est un thread cloisonné. Cet attribut doit être présent au point d'entrée de toute application qui utilise des Windows Forms ; s'il est omis, les composants Windows peuvent ne pas fonctionner correctement. Si l’attribut n’est pas présent, l’application utilise le modèle multithread cloisonné, qui n’est pas pris en charge pour les Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]les projets qui utilisent l’infrastructure d’application n’ont pas besoin de marquer la méthode **main** avec STAThread. Le [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilateur le fait automatiquement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, ajoutez l' <xref:System.STAThreadAttribute> attribut au point d’entrée. Si l' <xref:System.MTAThreadAttribute?displayProperty=fullName> attribut est présent, supprimez-le.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si vous développez pour le .NET Compact Framework, pour <xref:System.STAThreadAttribute> lequel l’attribut est inutile et n’est pas pris en charge.

## <a name="example"></a>Exemple
Les exemples suivants illustrent l’utilisation correcte <xref:System.STAThreadAttribute>de:

[!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
[!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]