---
title: 'CA2006 : Utilisez SafeHandle pour encapsuler les ressources natives'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0e671deab060346bb998932495e5590f19945eaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233104"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006 : Utilisez SafeHandle pour encapsuler les ressources natives

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Le code managé <xref:System.IntPtr> utilise pour accéder aux ressources natives.

## <a name="rule-description"></a>Description de la règle

L’utilisation `IntPtr` de dans du code managé peut indiquer un problème potentiel de sécurité et de fiabilité. Toutes les utilisations `IntPtr` de doivent être examinées pour déterminer si l’utilisation <xref:System.Runtime.InteropServices.SafeHandle> d’un ou d’une technologie similaire est requise à la place. Des problèmes se produisent si `IntPtr` le représente une ressource native, telle que la mémoire, un descripteur de fichier ou un socket, que le code managé est considéré comme propriétaire. Si le code managé possède la ressource, il doit également libérer les ressources natives qui lui sont associées, car cela entraînerait une fuite des ressources.

Dans de tels scénarios, des problèmes de sécurité ou de fiabilité se présenteront également si l’accès multithread `IntPtr` est autorisé à et un moyen de libérer la ressource représentée par `IntPtr` le est fourni. Ces problèmes impliquent le recyclage `IntPtr` de la valeur de la version de la ressource, tandis que l’utilisation simultanée de la ressource est effectuée sur un autre thread. Cela peut entraîner des conditions de concurrence où un thread peut lire ou écrire des données associées à la mauvaise ressource. Par exemple, si votre type stocke un handle du système `IntPtr` d’exploitation en tant que et permet aux utilisateurs d’appeler à la fois la méthode **Close** et toute autre méthode qui utilise ce handle simultanément et sans synchronisation, votre code présente un problème de recyclage des handles.

Ce problème de recyclage des handles peut entraîner une altération des données et, souvent, une faille de sécurité. `SafeHandle`et sa classe <xref:System.Runtime.InteropServices.CriticalHandle> sœur fournissent un mécanisme permettant d’encapsuler un handle natif vers une ressource afin que de tels problèmes de Threading puissent être évités. En outre, vous pouvez utiliser `SafeHandle` et sa classe `CriticalHandle` sœur pour d’autres problèmes liés aux threads, par exemple, pour contrôler avec soin la durée de vie des objets managés qui contiennent une copie du handle natif sur les appels aux méthodes natives. Dans ce cas, vous pouvez souvent supprimer des appels `GC.KeepAlive`à. La surcharge de performances que vous encourez `SafeHandle` lorsque vous utilisez et, dans une `CriticalHandle`moindre mesure, peut être souvent réduite par une conception soigneuse.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

`IntPtr` Convertit `SafeHandle` l’utilisation en pour gérer en toute sécurité l’accès aux ressources natives. Pour obtenir <xref:System.Runtime.InteropServices.SafeHandle> des exemples, consultez l’article de référence.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas cet avertissement.

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable>