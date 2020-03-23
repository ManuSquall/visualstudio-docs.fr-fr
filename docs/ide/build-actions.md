---
title: Actions de génération pour les fichiers
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35136ac0b7b0104f1812df7a9bf8ba81f6907374
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301985"
---
# <a name="build-actions"></a>Actions de génération

Tous les fichiers d’un projet Visual Studio ont une action de génération. L’action de génération contrôle ce qui arrive au fichier quand le projet est compilé.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Actions de génération dans Visual Studio pour Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Définir une action de génération

Pour définir l’action de génération concernant un fichier, ouvrez les propriétés du fichier dans la fenêtre **Propriétés** en le sélectionnant dans l’**Explorateur de solutions** et en appuyant sur **Alt**+**Entrée**. Vous pouvez aussi cliquer avec le bouton droit sur le fichier dans l’**Explorateur de solutions**, puis choisir **Propriétés**. Dans la fenêtre **Propriétés**, dans la section **Avancé**, utilisez la liste déroulante en regard d’**Action de génération** afin de définir une action de génération pour le fichier.

![Actions de génération pour un fichier dans Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Valeurs des actions de génération

Voici certaines des actions de génération les plus courantes pour les fichiers projet C# et Visual Basic :

|Action de génération | Types de projet | Description |
|-|-|
| **AdditionalFiles** | C#, Visual Basic | Fichier texte non-source passé au compilateur C# ou Visual Basic en tant qu’entrée. Cette action de génération est principalement utilisée pour fournir des entrées aux [analyseurs](../code-quality/roslyn-analyzers-overview.md) qui sont référencés par un projet pour vérifier la qualité du code. Pour plus d’informations, consultez [Utiliser des fichiers supplémentaires](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).|
| **ApplicationDefinition** | WPF | Fichier qui définit votre application. Quand vous créez un projet pour la première fois, il s’agit de *App.xaml*. |
| **CodeAnalysisDictionary** | .NET | Dictionnaire de mots personnalisés, utilisé par l’analyse du code pour la vérification orthographique. Voir [comment : Personnaliser le dictionnaire d’analyse de code](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Compiler** | n'importe laquelle | Le fichier est passé comme fichier source au compilateur.|
| **Contenu** | .NET | Un fichier marqué comme **Contenu** peut être récupéré sous la forme d’un flux par le biais d’un appel à <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. Pour les projets ASP.NET, ces fichiers sont ajoutés pour faire partie du site au moment de son déploiement.|
| **DesignData** | WPF | Utilisé pour les fichiers ViewModel XAML, pour permettre l’affichage des contrôles utilisateur au moment du design, avec des types factices et des exemples de données. |
| **DesignDataWithDesignTimeCreateable** | WPF | Semblable à **DesignData**, mais avec des types réels.  |
| **Ressource incorporée** | .NET | Le fichier est passé au compilateur comme ressource à incorporer dans l’assembly. Vous pouvez appeler <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> pour lire le fichier à partir de l’assembly.|
| **EntityDeploy** | .NET | Pour les fichiers .edmx Entity Framework (EF) qui spécifient le déploiement des artefacts EF. |
| **Fakes** | .NET | Utilisé pour l’infrastructure de test Microsoft Fakes. Voir [Isoler du code testé avec Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) |
| **Aucun** | n'importe laquelle | Le fichier ne fait pas du tout partie de la build. Cette valeur peut être utilisée pour les fichiers de documentation tels que les fichiers « Lisez-moi ».|
| **Page** | WPF | Compilez un fichier XAML à un fichier binaire .baml pour un chargement plus rapide au moment de l’exécution. |
| **Ressource** | WPF | Spécifie que le fichier doit être incorporé dans un fichier de ressources de manifeste d’assembly avec l’extension *.g.resources*. |
| **Ombre** | .NET | Utilisé pour un fichier .accessor qui contient une liste de noms de fichiers d’assembly générés, un par ligne. Pour chaque assembly de la liste, générez des classes publiques avec des noms `ClassName_Accessor` semblables aux originaux, mais avec des méthodes publiques au lieu de méthodes privées. Utilisé pour des tests unitaires. |
| **Écran d’éclaboussure** | WPF | Spécifie un fichier d’image à afficher au moment de la mise en place de l’application. |
| **XamlAppDef** | Windows Workflow Foundation | Indique à la build de générer un fichier XAML de workflow dans un assembly avec un flux de travail incorporé. |

> [!NOTE]
> D’autres actions de génération peuvent être définies pour des types de projet spécifiques. Par conséquent, la liste des actions de génération dépend du type de projet et des valeurs, qui ne figurent pas dans cette liste, peuvent apparaître.

## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Options du compilateur Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Actions de génération (Visual Studio pour Mac)](/visualstudio/mac/build-actions)
