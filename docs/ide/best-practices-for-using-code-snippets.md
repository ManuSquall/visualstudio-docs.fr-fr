---
title: Meilleures pratiques pour l'utilisation des extraits de code
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52845b2d8f08486f84422957ce8f38a95c1a4d31
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923679"
---
# <a name="best-practices-for-using-code-snippets"></a>Bonnes pratiques pour l’utilisation des extraits de code

Le code d’un extrait de code montre uniquement le moyen le plus simple de faire quelque chose. Dans la plupart des cas, le code doit être modifié pour s’adapter à l’application,

## <a name="handling-exceptions"></a>Gestion des exceptions

Habituellement, l’extrait de code Try...Catch empêche les interceptions et réinitialise toutes les exceptions. ce qui peut ne pas être le bon choix pour votre projet. Pour chaque exception, il existe plusieurs façons de répondre. Vous trouverez des exemples sur les pages [Guide pratique pour gérer une exception à l’aide de try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) et [Instruction Try... Catch... Finally (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Emplacements des fichiers

Lorsque vous adaptez des emplacements de fichiers à votre application, vous devez réfléchir à ce qui suit :

- Trouver un emplacement accessible. Les utilisateurs n’ayant pas forcément accès au dossier *Program Files* de l’ordinateur, il est possible que le stockage de fichiers avec les fichiers d’application ne fonctionne pas.

- Trouver un emplacement sécurisé. Le stockage des fichiers dans le dossier racine (*C:\\*) n’est pas sécurisé. Pour les données d’application, nous vous recommandons le dossier *Application Data*. Pour les données utilisateur, l’application peut créer un fichier pour chaque utilisateur dans le dossier *Documents*.

- Utiliser un nom de fichier valide. Vous pouvez utiliser les contrôles <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> pour réduire la probabilité d’avoir des noms de fichiers non valides. N’oubliez pas qu’entre le moment où l’utilisateur sélectionne un fichier et celui où votre code manipule ce fichier, ce dernier peut avoir été supprimé. En outre, l’utilisateur peut ne pas avoir les autorisations pour écrire dans le fichier.

## <a name="security"></a>Sécurité

Le niveau de sécurisation d’un extrait de code dépend de l’endroit où il est utilisé dans le code source et de la façon dont il est modifié une fois qu’il se trouve dans le code. La liste suivante contient quelques-uns des points qui doivent être pris en compte.

- Accès aux fichiers et aux bases de données

- Sécurité d'accès du code

- Protection des ressources (journaux des événements, Registre)

- Stockage de secrets

- Vérification des entrées

- Transmission des données aux outils de script

Pour plus d’informations, consultez la page [Sécuriser des applications](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Extraits de code téléchargés

Les extraits de code IntelliSense installés par Visual Studio ne constituent pas en eux-mêmes un risque de sécurité. Toutefois, ils peuvent entraîner des risques de sécurité dans votre application. Les extraits de code téléchargés sur Internet doivent être traités comme tout autre contenu téléchargé, c’est-à-dire avec une extrême prudence.

- Téléchargez des extraits de code uniquement à partir de sites de confiance et utilisez des logiciels antivirus à jour.

- Ouvrez tous les fichiers d’extrait de code téléchargés dans le Bloc-notes ou dans l’éditeur XML de Visual Studio, et examinez-les attentivement avant de les installer. Recherchez les problèmes potentiels suivants :

    - L’extrait de code est susceptible d’endommager votre système si vous l’exécutez. Lisez le code source attentivement avant de l’exécuter.

    - Le bloc concernant l’URL de l’aide du fichier d’extrait de code peut contenir des URL qui exécutent un fichier de script malveillant ou qui dirigent vers un site web malveillant.

    - L’extrait de code peut contenir des références qui sont ajoutées de manière silencieuse à votre projet et peuvent être chargées à tout endroit de votre système. Ces références peuvent avoir été téléchargées sur votre ordinateur à partir de l’endroit où vous avez téléchargé l’extrait de code. L’extrait de code peut ensuite appeler une méthode dans la référence qui exécute du code malveillant. Pour vous protéger de ce type d’attaque, examinez attentivement les blocs Imports et References du fichier d’extrait de code.

## <a name="see-also"></a>Voir aussi

- [Extraits de code IntelliSense Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Sécuriser des applications](../ide/securing-applications.md)
- [Extraits de code](../ide/code-snippets.md)