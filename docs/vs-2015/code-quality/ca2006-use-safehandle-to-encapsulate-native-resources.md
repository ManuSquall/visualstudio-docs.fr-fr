---
title: 'CA2006 : Utilisez SafeHandle pour encapsuler les ressources natives | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fdf3ff02c86a878e9c955d2b3b92879870700efa
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521145"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006 : Utilisez SafeHandle pour encapsuler les ressources natives
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Category|Microsoft. fiabilité|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Le code managé utilise <xref:System.IntPtr> pour accéder aux ressources natives.

## <a name="rule-description"></a>Description de la règle
 L’utilisation de `IntPtr` dans du code managé peut indiquer un problème potentiel de sécurité et de fiabilité. Toutes les utilisations de `IntPtr` doivent être examinées pour déterminer si l’utilisation d’un <xref:System.Runtime.InteropServices.SafeHandle> ou d’une technologie similaire est requise à la place. Des problèmes se produisent si le `IntPtr` représente une ressource native, telle que la mémoire, un descripteur de fichier ou un socket, que le code managé est considéré comme propriétaire. Si le code managé possède la ressource, il doit également libérer les ressources natives qui lui sont associées, car cela entraînerait une fuite des ressources.

 Dans de tels scénarios, des problèmes de sécurité ou de fiabilité se présenteront également si l’accès multithread est autorisé à `IntPtr` et un moyen de libérer la ressource représentée par le `IntPtr` est fourni. Ces problèmes impliquent le recyclage de la valeur de la version de la `IntPtr` ressource, tandis que l’utilisation simultanée de la ressource est effectuée sur un autre thread. Cela peut entraîner des conditions de concurrence où un thread peut lire ou écrire des données associées à la mauvaise ressource. Par exemple, si votre type stocke un handle du système d’exploitation en tant que `IntPtr` et permet aux utilisateurs d’appeler à la fois la méthode **Close** et toute autre méthode qui utilise ce handle simultanément et sans synchronisation, votre code présente un problème de recyclage des handles.

 Ce problème de recyclage des handles peut entraîner une altération des données et, souvent, une faille de sécurité. `SafeHandle`et sa classe sœur <xref:System.Runtime.InteropServices.CriticalHandle> fournissent un mécanisme permettant d’encapsuler un handle natif vers une ressource afin que de tels problèmes de Threading puissent être évités. En outre, vous pouvez utiliser `SafeHandle` et sa classe sœur `CriticalHandle` pour d’autres problèmes liés aux threads, par exemple, pour contrôler avec soin la durée de vie des objets managés qui contiennent une copie du handle natif sur les appels aux méthodes natives. Dans ce cas, vous pouvez souvent supprimer des appels à `GC.KeepAlive` . La surcharge de performances que vous encourez analyses lorsque vous utilisez `SafeHandle` et, dans une moindre mesure, `CriticalHandle` peut souvent être réduite par une conception soigneuse.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Convertit `IntPtr` l’utilisation en `SafeHandle` pour gérer en toute sécurité l’accès aux ressources natives. <xref:System.Runtime.InteropServices.SafeHandle>Pour obtenir des exemples, consultez la rubrique de référence.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous ne devez pas supprimer cet avertissement.

## <a name="see-also"></a>Voir aussi
 <xref:System.IDisposable>
