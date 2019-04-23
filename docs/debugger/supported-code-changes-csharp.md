---
title: Prise en charge des modifications de Code (C# et Visual Basic) | Microsoft Docs
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f20f61ffc4a6e4105a96b58c3dc73e7154e7c9cd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60055786"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Prise en charge des modifications de code (C# et Visual Basic)
Modifier &amp; Continuer gère la plupart des types de modifications du code dans le corps des méthodes. Toutefois, la plupart des modifications en dehors du corps des méthodes et quelques autres à l'intérieur ne peuvent pas s'appliquer pendant le débogage. Pour appliquer ces modifications non prises en charge, vous devez arrêter le débogage et redémarrer avec une version nouvelle du code.

## <a name="supported-changes-to-code"></a>Modifications prises en charge pour le code

Le tableau ci-dessous présente les modifications qui peuvent être passées à C# et le code Visual Basic pendant une session de débogage sans avoir à redémarrer la session.

|Fonctionnalité/élément de langage|Opération de modification pris en charge|Limitations|
|-|-|-|
|Types|Ajoutez les méthodes, champs, constructeurs, et al.|[Oui](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Ajouter ou modifier|Non|
|expressions d’async/await|Ajouter ou modifier|[Oui](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Objets dynamiques|Ajouter ou modifier|Non|
|expressions lambda|Ajouter ou modifier|[Oui](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Expressions LINQ|Ajouter ou modifier|[Identique à celui des expressions lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Nouvelles fonctionnalités de langage telles que l’interpolation de chaîne et opérateurs conditionnels null sont généralement pris en charge par Modifier & Continuer. Pour obtenir les informations les plus récentes, consultez le [Enc pris en charge modifie](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) page.

## <a name="unsupported-changes-to-code"></a>Modifications du code non pris en charge
 Impossible d’appliquer les modifications suivantes à C# et le code Visual Basic pendant une session de débogage :

- Modifications à l'instruction en cours ou à toute autre instruction active.

     Les instructions actives incluent toutes les instructions, dans les fonctions figurant dans la pile des appels, qui ont été appelées pour parvenir à l'instruction en cours.

     L'instruction en cours est marquée par un arrière-plan jaune dans la fenêtre source. D'autres instructions actives sont marquées par un arrière-plan grisé et sont en lecture seule. Ces couleurs par défaut peuvent être modifiées dans la boîte de dialogue **Options**.

- Le tableau suivant présente les modifications du code non pris en charge par l’élément de langage.

|Fonctionnalité/élément de langage|Opération de modification non pris en charge|
|-|-|
|Tous les éléments de code|Renommage|
|Espaces de noms|Ajouter|
|Espaces de noms, types, membres|Supprimer|
|Génériques|Ajouter ou modifier|
|Interfaces|Modifier|
|Types|Ajouter un membre abstrait ou virtuel, ajoutez remplacement (consultez [détails](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Types|Ajouter un destructeur|
|Membres|Modifier un membre faisant référence à un type interop incorporé|
|Membres (Visual Basic)|Modifier un membre avec l’instruction On Error ou Resume|
|Membres (Visual Basic)|Modifier un membre qui contient une clause de requête Aggregate, Group By, joindre Simple ou groupe joindre LINQ|
|Méthodes|Modifier les signatures|
|Méthodes|Rendre une méthode abstraite deviennent abstraites en ajoutant un corps de méthode|
|Méthodes|Supprimer le corps de méthode|
|Attributs|Ajouter ou modifier|
|Événements ou propriétés|Modifier un paramètre de type, le type de base, type délégué, ou type de retour |
|Les opérateurs ou les indexeurs|Modifier un paramètre de type, le type de base, type délégué, ou type de retour |
|catch (blocs)|Modifier lorsqu’elle contient une instruction active|
|blocs try-catch-finally|Modifier lorsqu’elle contient une instruction active|
|instructions Using|Ajouter|
|méthodes/lambdas asynchrones|Modifier une méthode/lambda async dans un projet ciblant .NET Framework 4 et réduire (consultez [détails](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Modifier un itérateur dans un projet ciblant .NET Framework 4 et réduire (consultez [détails](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|

## <a name="unsafe-code"></a>Code unsafe
 Les modifications apportées à du code unsafe présentent les mêmes restrictions que celles qui portent sur du code sécurisé, avec une restriction supplémentaire : Modifier & Continuer ne prend pas en charge les modifications apportées au code unsafe dans une méthode qui contient le `stackalloc` opérateur.

## <a name="unsupported-app-scenarios"></a>Scénarios d’application non pris en charge

Plateformes et applications non pris en charge incluent ASP.NET 5, Silverlight 5 et Windows 8.1.

> [!NOTE]
> Les applications qui sont prises en charge incluent UWP Windows 10 et les applications x86 et x64 qui ciblent le .NET Framework 4.6 bureau ou versions ultérieures (.NET Framework est une version de bureau uniquement).

## <a name="unsupported-scenarios"></a>Scénarios non pris en charge
 Modifier &amp; Continuer n'est pas disponible dans les scénarios de débogage suivants :

- Débogage en mode mixte (natif/managé).

- Débogage SQL.

- Débogage d’un dump Dr. Watson.

- Débogage d'une application runtime incorporée.

- Débogage d’une application à l’aide d’attacher au processus (**Déboguer > Attacher au processus**) au lieu d’exécuter l’application en choisissant **Démarrer** à partir de la **déboguer** menu.

- Débogage de code optimisé.

- Débogage d'une version ancienne de votre code après l'échec de génération d'une nouvelle version en raison d'erreurs de build.

## <a name="see-also"></a>Voir aussi
- [Modifier & Continuer (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Guide pratique pour utiliser Modifier et Continuer (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)