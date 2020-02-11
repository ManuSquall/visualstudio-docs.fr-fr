---
title: avertissements liés à l’interopérabilité
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: jillre
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1eb65f52df4b27837c00b7557db0c5e15e6c187
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091754"
---
# <a name="interoperability-warnings"></a>avertissements liés à l’interopérabilité

Les avertissements d’interopérabilité prennent en charge l’interaction avec les clients COM.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
| - | - |
| [CA1400 : Des points d’entrée P/Invoke doivent exister](../code-quality/ca1400.md) | Une méthode publique ou protégée est marquée avec l'attribut System.Runtime.InteropServices.DllImportAttribute. La bibliothèque non managée n'a pas pu être localisée, ou la méthode n'a pu être mise en correspondance avec aucune fonction de la bibliothèque. |
| [CA1401 : Les P/Invoke ne doivent pas être visibles](../code-quality/ca1401.md) | Une méthode publique ou protégée dans un type public a l’attribut System. Runtime. InteropServices. DllImportAttribute (également implémenté par le mot clé Declare dans Visual Basic). De telles méthodes ne doivent pas être exposées. |
| [CA1402 : Évitez les surcharges dans les interfaces COM visibles](../code-quality/ca1402.md) | Lorsque les méthodes surchargées sont exposées aux clients COM, seule la première surcharge de méthode conserve son nom. Les surcharges suivantes sont renommées de manière unique par l'ajout d'un trait de soulignement (_) au nom et d'un entier qui correspond à l'ordre de déclaration de la surcharge. |
| [CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM](../code-quality/ca1403.md) | Un type valeur visible par COM est marqué à l’aide de l’attribut System. Runtime. InteropServices. StructLayoutAttribute défini sur LayoutKind. auto. La disposition de ces types peut changer entre les versions de .NET, ce qui empêchera les clients COM qui attendent une disposition spécifique. |
| [CA1404 : Appeler GetLastError immédiatement après P/Invoke](../code-quality/ca1404.md) | Un appel est passé à la méthode Marshal. GetLastWin32Error ou à la fonction [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError équivalente, et l’appel immédiatement antérieur n’est pas une méthode d’appel de code non managé. |
| [CA1405 : Les types de base type visibles par COM doivent être visibles par COM](../code-quality/ca1405.md) | Un type visible par COM dérive d'un type qui n'est pas visible par COM. |
| [CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6](../code-quality/ca1406.md) | Les clients COM Visual Basic 6 ne peut pas accéder aux entiers de 64 bits. |
| [CA1407 : Éviter les membres statiques dans les types visibles par COM](../code-quality/ca1407.md) | COM ne prend pas en charge les méthodes statiques. |
| [CA1408 : N’utilisez pas le paramètre AutoDual ClassInterfaceType](../code-quality/ca1408.md) | Les types qui utilisent une interface double permettent aux clients de se lier à une disposition d'interface spécifique. Les modifications apportées à une version future de la disposition du type ou des types de base bloquent les clients COM qui se lient à l'interface. Par défaut, si l'attribut ClassInterfaceAttribute n'est pas spécifié, une interface de répartition uniquement est utilisée. |
| [CA1409 : Les types visibles par COM doivent pouvoir être créés](../code-quality/ca1409.md) | Un type référence marqué spécifiquement comme visible par des clients COM contient un constructeur public paramétré, mais ne contient pas de constructeur public par défaut (sans paramètre). Les clients COM ne peuvent pas créer de type sans constructeur public par défaut. |
| [CA1410 : Les méthodes d’inscription COM doivent être mises en correspondance](../code-quality/ca1410.md) | Un type déclare une méthode marquée à l’aide de l’attribut <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, mais ne déclare pas de méthode marquée à l’aide de l’attribut <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>, ou vice versa. |
| [CA1411 : Les méthodes d’inscription COM ne doivent pas être visibles](../code-quality/ca1411.md) | Une méthode marquée à l’aide de l’attribut System. Runtime. InteropServices. ComRegisterFunctionAttribute ou de l’attribut System. Runtime. InteropServices. ComUnregisterFunctionAttribute est visible de l’extérieur. |
| [CA1412 : Marquez les interfaces ComSource comme IDispatch](../code-quality/ca1412.md) | Un type est marqué avec l'attribut System.Runtime.InteropServices.ComSourceInterfacesAttribute et au moins une des interfaces spécifiées n'est pas marquée avec l'attribut System.Runtime.InteropServices.InterfaceTypeAttribute ayant la valeur ComInterfaceType.InterfaceIsIDispatch. |
| [CA1413 : Évitez les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413.md) | Les champs d'instance non publics des types valeur visibles par COM sont visibles par les clients COM. Passez en revue le contenu des champs pour voir les informations qui ne doivent pas être exposées, sinon vous aurez une conception imprévue ou des conséquences sur la sécurité. |
| [CA1414 : Marquer les arguments P/Invoke booléens comme MarshalAs](../code-quality/ca1414.md) | Le type de données booléen contient plusieurs représentations dans le code non managé. |
| [CA1415 : Déclarer correctement les méthodes P/Invoke](../code-quality/ca1415.md) | Cette règle recherche les déclarations de méthode d’appel de code non managé qui ciblent [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] fonctions qui ont un pointeur vers un paramètre de structure OVERLAPPED et le paramètre managé correspondant n’est pas un pointeur vers une structure <xref:System.Threading.NativeOverlapped?displayProperty=fullName>. |
