---
title: Prise en main avec les extensions du service de langage et de l’éditeur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7894efc477e0c406cf8e85f4d3d31df4f2ef97c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711309"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Prise en main du service de langage et des extensions de l’éditeur
Vous pouvez utiliser les extensions de l’éditeur pour ajouter des fonctionnalités du service de langage telles que le mode plan, la correspondance des accolades, IntelliSense et les ampoules à votre propre langage de programmation ou à n’importe quel type de contenu. Vous pouvez également personnaliser l’apparence et le comportement de l’éditeur Visual Studio, par exemple la coloration du texte, les marges, les ornements et d’autres éléments visuels. Vous pouvez également définir votre propre type de contenu et spécifier l’apparence et le comportement des affichages de texte dans lesquels votre contenu apparaît.

 Pour commencer à écrire des extensions de l’éditeur, utilisez les modèles de projet de l’éditeur qui sont installés dans le cadre du kit de développement logiciel (SDK) Visual Studio. Le kit de développement logiciel (SDK) Visual Studio est un ensemble d’outils téléchargeables qui facilitent le développement d’extensions Visual Studio, soit à l’aide de VSPackages, soit à l’aide de l’Managed Extensibility Framework (MEF).

> [!NOTE]
> Pour plus d’informations sur le kit de développement logiciel (SDK) Visual Studio, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Nous vous recommandons d’en savoir plus sur les concepts et technologies suivants avant d’écrire vos propres extensions d’éditeur.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Extensions du Windows Presentation Foundation (WPF) et de l’éditeur
 L’interface utilisateur de l’éditeur Visual Studio est implémentée à l’aide de l’Windows Presentation Foundation (WPF). WPF offre une expérience visuelle riche et un modèle de programmation cohérent qui sépare les aspects visuels du code de la logique métier. Vous pouvez utiliser de nombreux éléments et fonctionnalités WPF lorsque vous créez des extensions d’éditeur. Pour plus d’informations, consultez [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) et extensions de l’éditeur
 L’éditeur Visual Studio utilise le Managed Extensibility Framework (MEF) pour gérer ses composants et extensions. Le MEF permet également aux développeurs de créer plus facilement des extensions pour une application hôte telle que Visual Studio. Dans ce Framework, vous définissez une extension en fonction d’un contrat MEF et l’exportez en tant que composant MEF. L’application hôte gère les composants en les recherchant, en les inscrivant et en veillant à ce qu’ils soient appliqués au contexte correct.

> [!NOTE]
> Pour plus d’informations sur le MEF dans l’éditeur, consultez [Managed Extensibility Framework dans l’éditeur](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Extensions et points d’extension de l’éditeur Visual Studio
 Les points d’extension de l’éditeur sont des composants MEF que vous pouvez personnaliser et étendre. Dans certains cas, vous étendez le point d’extension en implémentant une interface et en l’exportant avec les métadonnées appropriées. Dans d’autres cas, vous déclarez simplement une extension et l’exportez en tant que type particulier.

 Voici quelques-uns des types de base des extensions d’éditeur :

- Marges et barres de défilement

- Balises

- Ornements

- Options

- IntelliSense

  Pour plus d’informations sur les points d’extension de l’éditeur, consultez [service de langage et points d’extension](../extensibility/language-service-and-editor-extension-points.md)de l’éditeur.

## <a name="deploying-editor-extensions"></a>Déploiement des extensions de l’éditeur
 Dans Visual Studio, vous déployez des extensions d’éditeur en ajoutant un fichier de métadonnées nommé *source. extension. vsixmanifest* à la solution, en générant la solution, puis en ajoutant une copie des fichiers binaires et du manifeste dans un dossier connu de Visual Studio. Le fichier manifeste définit les faits de base relatifs à l’extension (par exemple, nom, auteur, version et type de contenu). Pour plus d’informations sur le fichier manifeste VSIX et sur le déploiement des extensions, consultez [Envoyer des extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Quand vous installez une extension sur un ordinateur, incluez les fichiers binaires et le manifeste dans un sous-dossier du dossier connu de Visual Studio.

> [!WARNING]
> Vous n’avez pas à vous soucier des détails des manifestes et des emplacements de déploiement si vous utilisez l’un des modèles d’extensibilité de l’éditeur inclus dans Visual Studio. Les modèles contiennent tout ce qui est nécessaire pour inscrire et déployer une extension.

## <a name="run-extensions-in-the-experimental-instance"></a>Exécuter des extensions dans l’instance expérimentale
 Vous pouvez isoler votre version de travail de Visual Studio pendant que vous développez une extension en la déployant dans le dossier expérimental suivant (sur Windows Vista et Windows 7) :

 *{% LOCALAPPDATA%} \VisualStudio\10.0Exp\Extensions \\ {Company} \\ {ExtensionID}*

 où *% LocalAppData%* est le nom de l’utilisateur connecté, *Company* est le nom de la société qui possède l’extension et *ExtensionID* est l’ID de l’extension.

 Lorsque vous déployez une extension à l’emplacement expérimental, elle s’exécute en mode débogage. Une deuxième instance de Visual Studio est démarrée et est nommée **Microsoft Visual Studio instance expérimentale**.

## <a name="manage-extensions"></a>Gérer les extensions
 Les extensions de Visual Studio sont répertoriées dans **extensions et mises à jour** (dans le menu **Outils** ). Si vous testez une extension dans l’instance expérimentale, elle est répertoriée dans **extensions et mises à jour** dans l’instance expérimentale, mais elle n’est pas répertoriée dans l’instance de développement.

 Pour plus d’informations, consultez [Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Utiliser des modèles pour créer des extensions d’éditeur
 Vous pouvez utiliser les modèles de l’éditeur pour créer des extensions MEF qui personnalisent les classifieurs, les ornements et les marges. Il existe des modèles pour les projets C# et Visual Basic. Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 Vous pouvez également utiliser le modèle de projet VSIX pour créer des extensions. Ce modèle fournit uniquement les éléments qui sont requis pour déployer tout type d’extension, et inclut le fichier *source. extension. vsixmanifest* , les références d’assembly requises et un fichier projet qui inclut les tâches de génération qui vous permettent de déployer l’extension. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).

 Vous pouvez également créer des composants de l’éditeur MEF à partir d’une extension de package Visual Studio. Pour plus d’informations, consultez les procédures pas à pas suivantes :

- [Procédure pas à pas : utilisation d’une commande shell avec une extension d’éditeur](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Procédure pas à pas : utilisation d’une touche de raccourci avec une extension d’éditeur](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Voir aussi
- [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
