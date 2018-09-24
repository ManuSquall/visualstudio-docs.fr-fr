---
title: Mise en route avec le Service de langage et les Extensions de l’éditeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c07d2f374890d6a87b5fe45304d098acfb05065b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498378"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Bien démarrer avec les extensions d’éditeur et de service de langage
Vous pouvez utiliser des extensions de l’éditeur pour ajouter des fonctionnalités de service de langage telles que le mode plan, correspondance des accolades, IntelliSense et des ampoules à votre propre langage de programmation ou à n’importe quel type de contenu. Vous pouvez également personnaliser l’apparence et le comportement de l’éditeur Visual Studio, par exemple le texte de coloration, marges, les ornements et les autres éléments visuels. Vous pouvez également définir votre propre type de contenu et spécifier l’apparence et le comportement des vues de texte dans lequel votre contenu s’affiche.  
  
 Pour commencer à écrire des extensions de l’éditeur, utilisez les modèles de projet d’éditeur qui sont installés dans le cadre du SDK Visual Studio. Le SDK Visual Studio est un ensemble téléchargeable d’outils qui facilitent le développement d’extensions Visual Studio, à l’aide de VSPackages ou à l’aide de Managed Extensibility Framework (MEF).  
  
> [!NOTE]
>  Pour plus d’informations sur le SDK Visual Studio, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 Nous recommandons que vous en savoir plus sur les concepts suivants et les technologies avant d’écrire vos propres extensions de l’éditeur.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Les extensions d’éditeur et de Windows Presentation Foundation (WPF)  
 L’interface utilisateur de l’éditeur Visual Studio (IU) est implémentée à l’aide de Windows Presentation Foundation (WPF). WPF fournit une expérience visuelle riche et un modèle de programmation cohérent qui sépare les aspects visuels du code de la logique métier. Vous pouvez utiliser de nombreux éléments WPF et les fonctionnalités lorsque vous créez des extensions de l’éditeur. Pour plus d’informations, consultez [Windows Presentation Foundation](/dotnet/framework/wpf/index).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Les extensions d’éditeur et de Managed Extensibility Framework (MEF)  
 L’éditeur Visual Studio utilise Managed Extensibility Framework (MEF) pour gérer ses composants et les extensions. MEF permet également aux développeurs plus de créer facilement des extensions pour une application hôte, tel que Visual Studio. Dans cette infrastructure, vous allez définir une extension en fonction d’un contrat MEF et exportez-le en tant que composant MEF. L’application hôte gère les éléments par recherche les, leur inscription et s’assurer qu’elles sont appliquées au contexte correct.  
  
> [!NOTE]
>  Pour plus d’informations sur MEF dans l’éditeur, consultez [Managed Extensibility Framework dans l’éditeur](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Extensions et le points d’extension Éditeur visual Studio  
 Points d’extension éditeur sont des composants MEF que vous pouvez personnaliser et étendre. Dans certains cas, vous étendez le point d’extension en implémentant une interface et en exportant ainsi que les métadonnées correctes. Dans d’autres cas vous simplement déclarez une extension et exportez en tant qu’un type particulier.  
  
 Voici quelques-uns des types de base des extensions de l’éditeur :  
  
-   Marges et les barres de défilement  
  
-   Balises  
  
-   Ornements  
  
-   Options  
  
-   IntelliSense  
  
 Pour plus d’informations sur les points d’extension de l’éditeur, consultez [points d’extension éditeur et le service de langage](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Déploiement d’extensions de l’éditeur  
 Dans Visual Studio, vous déployez des extensions de l’éditeur en ajoutant un fichier de métadonnées nommé *source.extension.vsixmanifest* à la solution, génération de la solution et l’ajout d’une copie des fichiers binaires et le manifeste dans un dossier connu pour Visual Studio. Le fichier manifest définit les faits de base sur l’extension (par exemple, nom, auteur, version et type de contenu). Pour plus d’informations sur le fichier de manifeste VSIX et comment déployer des extensions, consultez [extensions Ship Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Lorsque vous installez une extension sur un ordinateur, inclure les fichiers binaires et le manifeste dans un sous-dossier du dossier qui est connue pour Visual Studio.  
  
> [!WARNING]
>  Vous n’avez pas à vous soucier des détails des manifestes et les emplacements de déploiement si vous utilisez un des modèles d’extensibilité éditeur qui sont inclus dans Visual Studio. Les modèles contiennent tout ce qui est nécessaire pour vous inscrire et déployer une extension.  
  
## <a name="run-extensions-in-the-experimental-instance"></a>Exécuter des extensions dans l’instance expérimentale  
 Vous pouvez isoler votre version de travail de Visual Studio pendant que vous développez une extension en le déployant dans le dossier suivant expérimental (sur Windows Vista et Windows 7) :  
  
 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Extensions\\{company}\\{ExtensionID}*  
  
 où *% LocalAppData%* est le nom de l’utilisateur connecté, *entreprise* est le nom de l’entreprise qui possède l’extension, et *ExtensionID* est l’ID de l’extension.  
  
 Lorsque vous déployez une extension à l’emplacement expérimentale, il s’exécute en mode débogage. Une deuxième instance de Visual Studio est démarrée et est nommée **Microsoft Visual Studio - Instance expérimentale**.  
  
## <a name="manage-extensions"></a>Gérer les extensions  
 Extensions pour Visual Studio sont répertoriées dans **Extensions et mises à jour** (sur le **outils** menu). Si vous testez une extension dans l’instance expérimentale, il est répertorié dans **Extensions et mises à jour** dans l’instance expérimentale, mais n’est ne pas répertorié dans l’instance de développement.  
  
 Pour plus d’informations, consultez [rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="use-templates-to-create-editor-extensions"></a>Utiliser des modèles pour créer des extensions de l’éditeur  
 Vous pouvez utiliser des modèles de l’éditeur pour créer des extensions MEF qui personnalisent les classifieurs, les ornements et les marges. Il existe des modèles pour les projets c# et Visual Basic. Pour plus d’informations, consultez [créer une extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 Vous pouvez également utiliser le modèle de projet VSIX pour créer des extensions. Ce modèle fournit uniquement les éléments qui sont nécessaires pour déployer n’importe quel type d’extension et inclure le *source.extension.vsixmanifest* fichier, les références d’assembly nécessaires et un fichier de projet qui inclut les tâches de génération qui permettent de déployer l’extension. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).  
  
 Vous pouvez également créer éditeur composants MEF à partir d’une extension de Package Visual Studio. Les procédures suivantes pour plus d’informations, consultez :  
  
-   [Procédure pas à pas : En utilisant une commande de l’interpréteur de commandes avec une extension de l’éditeur](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Procédure pas à pas : Utilisation d’une touche de raccourci avec une extension de l’éditeur](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension éditeur et le service de langage](../extensibility/language-service-and-editor-extension-points.md)