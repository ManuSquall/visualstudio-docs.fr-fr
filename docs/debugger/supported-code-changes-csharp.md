---
title: Modifications du code prises en charge (C# et Visual Basic) | Microsoft Docs
description: Comprenez les modifications de code prises en charge lorsque vous utilisez la fonctionnalité Modifier & Continuer lors du débogage d’un projet C# ou Visual Basic dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/11/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 4fc3f49038a44b2b2bd5b467d6e1874f8a9a9803
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940759"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Modifications de code prises en charge (C# et Visual Basic)
Modifier &amp; Continuer gère la plupart des types de modifications du code dans le corps des méthodes. Toutefois, la plupart des modifications en dehors du corps des méthodes et quelques autres à l'intérieur ne peuvent pas s'appliquer pendant le débogage. Pour appliquer ces modifications non prises en charge, vous devez arrêter le débogage et redémarrer avec une version nouvelle du code.

## <a name="supported-changes-to-code"></a>Modifications de code prises en charge

Le tableau ci-dessous montre les modifications qui peuvent être apportées à C# et Visual Basic code pendant une session de débogage sans redémarrer la session.

|Élément ou fonctionnalité de langage|Opération de modification prise en charge|Limites|
|-|-|-|
|Types|Ajouter des méthodes, des champs, des constructeurs, et al|[Oui](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Iterators|Ajouter ou modifier|Non|
|expressions Async/await|Ajouter ou modifier|[Oui](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Objets dynamiques|Ajouter ou modifier|Non|
|expressions lambda|Ajouter ou modifier|[Oui](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Expressions LINQ|Ajouter ou modifier|[Identique aux expressions lambda](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|

> [!NOTE]
> Les nouvelles fonctionnalités de langage telles que l’interpolation de chaîne et les opérateurs conditionnels NULL sont généralement prises en charge par modifier & continuer. Pour obtenir les informations les plus récentes, consultez la page [modifications prises en charge par enc](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md) .

## <a name="unsupported-changes-to-code"></a>Modifications du code non prises en charge
 Les modifications suivantes ne peuvent pas être appliquées à C# et Visual Basic code pendant une session de débogage :

- Modifications à l'instruction en cours ou à toute autre instruction active.

     Les instructions actives incluent toutes les instructions, dans les fonctions figurant dans la pile des appels, qui ont été appelées pour parvenir à l'instruction en cours.

     L'instruction en cours est marquée par un arrière-plan jaune dans la fenêtre source. D'autres instructions actives sont marquées par un arrière-plan grisé et sont en lecture seule. Ces couleurs par défaut peuvent être modifiées dans la boîte de dialogue **Options**.

- Le tableau suivant montre les modifications non prises en charge de code par élément de langage.

|Élément ou fonctionnalité de langage|Opération de modification non prise en charge|
|-|-|
|Tous les éléments de code|Renommage|
|Espaces de noms|Ajouter|
|Espaces de noms, types, membres|DELETE|
|Génériques|Ajouter ou modifier|
|Interfaces|Modifier|
|Types|Ajouter un membre abstrait ou virtuel, ajouter un remplacement (voir les [Détails](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|
|Types|Ajouter un destructeur|
|Membres|Modifier un membre référençant un type Interop incorporé|
|Membres|Modifier un membre statique après qu’il a déjà été accédé en exécutant du code|
|Membres (Visual Basic)|Modifier un membre avec l’instruction On Error ou Resume|
|Membres (Visual Basic)|Modifier un membre contenant une clause de requête LINQ Aggregate, Group by, simple JOIN ou Group Join|
|Méthodes|Modifier les signatures|
|Méthodes|Rendre une méthode abstraite non abstraite en ajoutant un corps de méthode|
|Méthodes|Supprimer le corps de la méthode|
|Attributs|Ajouter ou modifier|
|Événements ou propriétés|Modifier un paramètre de type, un type de base, un type délégué ou un type de retour |
|Opérateurs ou indexeurs|Modifier un paramètre de type, un type de base, un type délégué ou un type de retour |
|catch (blocs)|Modifier le moment où il contient une instruction active|
|blocs try-catch-finally|Modifier le moment où il contient une instruction active|
|instructions Using|Ajouter|
|Méthodes Async/expressions lambda|Modifier une méthode Async/lambda dans un projet ciblant .NET Framework 4 et versions antérieures (voir les [Détails](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|
|Iterators|Modifier un itérateur dans un projet ciblant .NET Framework 4 et versions antérieures (voir les [Détails](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|

## <a name="unsafe-code"></a>Code unsafe
 Les modifications apportées à du code unsafe présentent les mêmes restrictions que celles qui portent sur du code sécurisé, avec une restriction supplémentaire : Modifier &amp; Continuer ne prend pas en charge les modifications de code unsafe dans une méthode qui contient l'opérateur `stackalloc`.

## <a name="unsupported-app-scenarios"></a>Scénarios d’application non pris en charge

Les applications et les plateformes non prises en charge incluent ASP.NET 5, Silverlight 5 et Windows 8.1.

> [!NOTE]
> Les applications prises en charge incluent UWP dans Windows 10, et les applications x86 et x64 qui ciblent le .NET Framework 4,6 ou les versions ultérieures (le .NET Framework est une version de bureau uniquement).

## <a name="unsupported-scenarios"></a>Scénarios non pris en charge
 Modifier &amp; Continuer n'est pas disponible dans les scénarios de débogage suivants :

- Débogage en mode mixte (natif/managé).

- Débogage SQL.

- Débogage d’un vidage Dr. Watson.

- Débogage d'une application runtime incorporée.

- Débogage d’une application à l’aide de l’option attacher au processus (**Déboguer > attacher au processus**) au lieu d’exécuter l’application en choisissant **Démarrer** dans le menu **Déboguer** .

- Débogage de code optimisé.

- Débogage d'une version ancienne de votre code après l'échec de génération d'une nouvelle version en raison d'erreurs de build.

## <a name="see-also"></a>Voir aussi
- [Modifier &amp; Continuer (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Guide pratique pour utiliser Modifier & Continuer (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)