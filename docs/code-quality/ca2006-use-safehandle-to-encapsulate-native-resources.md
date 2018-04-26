---
title: 'CA2006 : Utilisez SafeHandle pour encapsuler les ressources natives'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 4183828b4deddede919ea30db825e65f0360adef
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006 : Utilisez SafeHandle pour encapsuler les ressources natives
|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Le code managé utilise <xref:System.IntPtr> pour accéder aux ressources natives.

## <a name="rule-description"></a>Description de la règle
 Utilisation de `IntPtr` dans le code managé peut indiquer un problème potentiel de sécurité et de fiabilité. Toutes les utilisations de `IntPtr` doivent être examinées pour déterminer si l’utilisation d’un <xref:System.Runtime.InteropServices.SafeHandle> , ou une technologie similaire, est nécessaire à la place. Des problèmes seront produit si le `IntPtr` représente une ressource native, telles que la mémoire, un descripteur de fichier ou un socket, que le code managé est considérée comme propre. Si le code managé est propriétaire de la ressource, il doit également libérer les ressources natives qui lui est associés, car un échec de cette opération entraînerait une fuite de ressource.

 Dans de tels scénarios, des problèmes de sécurité ou de fiabilité existeront également si l’accès multithread est autorisé au `IntPtr` et un moyen de libérer la ressource représentée par le `IntPtr` est fournie. Ces problèmes impliquent le recyclage de le `IntPtr` valeur sur la version de la ressource lors de l’utilisation simultanée de la ressource est rendue sur un autre thread. Cela peut entraîner des conditions de concurrence où un thread peut lire ou écrire des données qui sont associées à la ressource incorrecte. Par exemple, si votre type stocke un handle de système d’exploitation comme un `IntPtr` et permet aux utilisateurs d’appeler à la fois **fermer** et toute autre méthode qui utilise ce handle sans une sorte de synchronisation et simultanément, votre code a une poignée de recyclage problème.

 Ce problème de recyclage de handle peut provoquer une altération des données et, souvent, une faille de sécurité. `SafeHandle` et sa classe sœur <xref:System.Runtime.InteropServices.CriticalHandle> fournissent un mécanisme pour encapsuler un handle natif à une ressource afin que ces problèmes de thread peuvent être évitées. En outre, vous pouvez utiliser `SafeHandle` et sa classe sœur `CriticalHandle` pour d’autres problèmes de thread, par exemple, pour contrôler avec soin la durée de vie des objets managés contenant une copie du handle natif sur les appels aux méthodes natives. Dans ce cas, vous pouvez souvent supprimer des appels à `GC.KeepAlive`. Le performances charge subie lorsque vous utilisez `SafeHandle` et, à un moindre degré, `CriticalHandle`, peut souvent être réduite avec une conception rigoureuse.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Convertir `IntPtr` utilisation de `SafeHandle` pour gérer en toute sécurité l’accès aux ressources natives. Consultez le <xref:System.Runtime.InteropServices.SafeHandle> rubrique de référence pour obtenir des exemples.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous ne devez pas supprimer cet avertissement.

## <a name="see-also"></a>Voir aussi
 <xref:System.IDisposable>