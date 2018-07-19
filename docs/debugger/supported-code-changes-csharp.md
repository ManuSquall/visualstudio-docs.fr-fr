---
title: Prise en charge des modifications de Code (c# et Visual Basic) | Documents Microsoft
ms.custom: ''
ms.date: 10/11/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 855e8111721480b98c1395811090a54dd6e3ab2a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480532"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Modifications de code prises en charge (c# et Visual Basic)
Modifier & Continuer gère la plupart des types de modifications du code dans le corps des méthodes. Toutefois, la plupart des modifications en dehors du corps des méthodes et quelques autres à l'intérieur ne peuvent pas s'appliquer pendant le débogage. Pour appliquer ces modifications non prises en charge, vous devez arrêter le débogage et redémarrer avec une version nouvelle du code.

## <a name="supported-changes-to-code"></a>Prise en charge des modifications de code

Le tableau ci-dessous indique les modifications qui peuvent être effectuées dans le code c# et Visual Basic pendant une session de débogage sans redémarrer la session.

|Élément de langage ou une fonctionnalité|Opération de modification pris en charge|Limitations|
|-|-|-|
|Types|Ajouter des méthodes, champs, constructeurs, et al.|[Oui](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Ajouter ou modifier|Non|
|expressions asynchrones / d’attente|Ajouter ou modifier|[Oui](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Objets dynamiques|Ajouter ou modifier|Non|
|expressions lambda|Ajouter ou modifier|[Oui](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Expressions LINQ|Ajouter ou modifier|[Identique à celui des expressions lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Nouvelles fonctionnalités de langage telles que l’interpolation de chaîne et opérateurs conditionnels null sont généralement prises en charge par Modifier & Continuer. Pour obtenir les informations les plus récentes, consultez le [Enc pris en charge modifie](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) page.

## <a name="unsupported-changes-to-code"></a>Modifications du code non pris en charge
 Les modifications suivantes ne peut pas être appliquées au code c# et Visual Basic pendant une session de débogage :  
  
-   Modifications à l'instruction en cours ou à toute autre instruction active.  
  
     Les instructions actives incluent toutes les instructions, dans les fonctions figurant dans la pile des appels, qui ont été appelées pour parvenir à l'instruction en cours.  
  
     L'instruction en cours est marquée par un arrière-plan jaune dans la fenêtre source. D'autres instructions actives sont marquées par un arrière-plan grisé et sont en lecture seule. Ces couleurs par défaut peuvent être modifiées dans le **Options** boîte de dialogue.

- Le tableau suivant présente les modifications du code non pris en charge par l’élément de langage.

|Élément de langage ou une fonctionnalité|Opération de modification non prise en charge|
|-|-|
|Tous les éléments de code|Renommage|
|Espaces de noms|Ajouter|
|Espaces de noms, types, membres|Supprimer|
|Génériques|Ajouter ou modifier|
|Interfaces|Modifier|
|Types|Ajouter un membre abstrait ou virtuel, ajoutez de remplacement (voir [détails](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Types|Ajouter un destructeur|
|Membres|Modifier un membre faisant référence à un type interop incorporé|
|Membres (Visual Basic)|Modifier un membre avec l’instruction On Error ou Resume|
|Membres (Visual Basic)|Modifier un membre contenant une clause de requête Aggregate, Group By, Join Simple ou LINQ de jointure de groupe|
|Méthodes|Modifier des signatures|
|Méthodes|Rendre une méthode abstraite deviennent abstraites en ajoutant un corps de méthode|
|Méthodes|Supprimer le corps de la méthode|
|Attributs|Ajouter ou modifier|
|Événements ou propriétés|Modifier un paramètre de type, le type de base, type délégué ou type de retour |
|Opérateurs ou des indexeurs|Modifier un paramètre de type, le type de base, type délégué ou type de retour |
|catch (blocs)|Modifier lorsqu’elle contient une instruction active|
|blocs try-catch-finally|Modifier lorsqu’elle contient une instruction active|
|instructions Using|Ajouter|
|méthodes/lambdas asynchrones|Modifier une méthode/lambda async dans un projet ciblant .NET Framework 4 et diminuer (voir [détails](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Modifier un itérateur dans un projet ciblant .NET Framework 4 et diminuer (voir [détails](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
  
## <a name="unsafe-code"></a>Code unsafe  
 Les modifications apportées à du code unsafe présentent les mêmes restrictions que celles qui portent sur du code sécurisé, avec une restriction supplémentaire : Modifier & Continuer ne prend pas en charge les modifications de code unsafe dans une méthode qui contient l'opérateur `stackalloc`.  

## <a name="unsupported-app-scenarios"></a>Scénarios d’application non pris en charge

Plateformes et des applications non prises en charge incluent ASP.NET 5, Silverlight 5 et Windows 8.1.

> [!NOTE]
> Les applications qui sont prises en charge sont notamment UWP dans Windows 10 et x86 et x64 des applications qui ciblent le .NET Framework 4.6 bureau ou versions ultérieures (.NET Framework est une version de bureau).
  
## <a name="unsupported-scenarios"></a>Scénarios non pris en charge  
 Modifier & Continuer n'est pas disponible dans les scénarios de débogage suivants :  
  
-   Débogage en mode mixte (natif/managé).  
  
-   Débogage SQL.  
  
-   Débogage d'un dump Dr. Watson.  
  
-   Débogage d'une application runtime incorporée.  
  
-   Débogage d’une application à l’aide d’attacher au processus (**Déboguer > Attacher au processus**) au lieu d’exécuter l’application en choisissant **Démarrer** à partir de la **déboguer** menu.  
  
-   Débogage de code optimisé.  
  
-   Débogage d'une version ancienne de votre code après l'échec de génération d'une nouvelle version en raison d'erreurs de build.
  
## <a name="see-also"></a>Voir aussi  
 [Modifier & Continuer (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Guide pratique pour utiliser Modifier & Continuer (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)