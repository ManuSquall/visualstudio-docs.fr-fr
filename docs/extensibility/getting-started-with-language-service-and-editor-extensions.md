---
title: "Prise en main de Service de langage et les Extensions de l’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5f7b7440ff2f42eba1d138872071d4e51d2402c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Prise en main de Service de langage et les Extensions de l’éditeur
Vous pouvez utiliser des extensions de l’éditeur pour ajouter des fonctionnalités de service de langage telles que le mode plan, la correspondance des accolades, IntelliSense et les ampoules pour votre propre langage de programmation ou à n’importe quel type de contenu. Vous pouvez également personnaliser l’apparence et le comportement de l’éditeur Visual Studio, par exemple texte coloration, les marges, les ornements et les autres éléments visuels. Vous pouvez également définir votre propre type de contenu et spécifier l’apparence et le comportement des vues de texte dans laquelle votre contenu s’affiche.  
  
 Pour commencer l’écriture d’extensions de l’éditeur, utilisez les modèles de projet d’éditeur qui sont installés dans le cadre du SDK Visual Studio. Le Kit de développement logiciel Visual Studio est un ensemble de télécharger des outils qui facilitent le développement d’extensions Visual Studio, à l’aide des VSPackages ou à l’aide de Managed Extensibility Framework (MEF).  
  
> [!NOTE]
>  Pour plus d’informations sur le SDK Visual Studio, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 Il est recommandé que vous en savoir plus sur les technologies et les concepts suivants avant d’écrire vos propres extensions de l’éditeur.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) et les Extensions de l’éditeur  
 L’interface utilisateur du éditeur Visual Studio (UI) est implémentée à l’aide de Windows Presentation Foundation (WPF). WPF fournit une expérience visuelle riche et un modèle de programmation cohérent qui sépare les aspects visuels du code à partir de la logique métier. Lorsque vous créez des extensions de l’éditeur, vous pouvez utiliser plusieurs éléments WPF et les fonctionnalités. Pour plus d’informations, consultez [Windows Presentation Foundation](/dotnet/framework/wpf/index).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) et les Extensions de l’éditeur  
 L’éditeur Visual Studio utilise Managed Extensibility Framework (MEF) pour gérer les composants et ses extensions. MEF permet également aux développeurs plus de créer facilement des extensions pour une application hôte, tel que Visual Studio. Dans ce cadre, vous définissez une extension en fonction d’un contrat MEF et exportez en tant que composant MEF. L’application hôte gère les éléments par recherche les, les inscrire et s’assurer qu’elles sont appliquées dans le contexte correct.  
  
> [!NOTE]
>  Pour plus d’informations sur MEF dans l’éditeur, consultez [Managed Extensibility Framework dans l’éditeur](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Points d’Extension de l’éditeur Visual Studio et des Extensions  
 Éditeur des points d’extension sont des composants MEF que vous pouvez personnaliser et étendre. Dans certains cas, vous étendez le point d’extension en implémentant une interface et en exportant avec les métadonnées correctes. Dans d’autres cas vous simplement déclarez une extension et les exportez sous la forme d’un type particulier.  
  
 Voici quelques-uns des types d’extensions de l’éditeur de base :  
  
-   Les marges et les barres de défilement  
  
-   Balises  
  
-   Ornements  
  
-   Options  
  
-   IntelliSense  
  
 Pour plus d’informations sur les points d’extension de l’éditeur, consultez [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Déploiement d’Extensions de l’éditeur  
 Dans Visual Studio, vous déployez des extensions de l’éditeur en lui ajoutant un fichier de métadonnées nommé source.extension.vsixmanifest à la solution, générer la solution, puis une copie des fichiers binaires et le manifeste dans un dossier connu vers Visual Studio. Le fichier manifeste définit les faits de base sur l’extension (par exemple, nom, auteur, version et type de contenu). Pour plus d’informations sur le fichier manifest VSIX et comment déployer des extensions, consultez [de livraison des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Lorsque vous installez une extension sur un ordinateur, inclure les fichiers binaires et le manifeste dans un sous-dossier du dossier qui est connu pour Visual Studio.  
  
> [!WARNING]
>  Vous n’avez pas à vous soucier des détails des manifestes et emplacements de déploiement si vous utilisez un des modèles d’extensibilité de l’éditeur qui sont inclus dans Visual Studio. Les modèles contiennent tout ce qui est requis pour enregistrer et déployer une extension.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Extensions en cours d’exécution dans l’Instance expérimentale  
 Vous pouvez isoler votre version de travail de Visual Studio lorsque vous développez une extension en la déployant dans le dossier suivant expérimental (sur Windows Vista et Windows 7) :  
  
 *%LocalAppData%*\VisualStudio\10.0Exp\Extensions\\*société*\\*ExtensionID*  
  
 où *%LocalAppData%* est le nom de l’utilisateur connecté, *société* est le nom de la société qui possède l’extension, et *ExtensionID* est l’ID de l’extension.  
  
 Lorsque vous déployez une extension à l’emplacement expérimentale, il s’exécute en mode débogage. Une deuxième instance de Visual Studio est démarrée et est nommée **Microsoft Visual Studio - Instance expérimentale**.  
  
## <a name="managing-extensions"></a>La gestion des extensions  
 Extensions pour Visual Studio sont répertoriées dans **Extensions et mises à jour** (sur le **outils** menu). Si vous testez une extension dans l’instance expérimentale, il est répertorié dans **Extensions et mises à jour** dans l’instance expérimentale, mais n’est ne pas répertorié dans l’instance de développement.  
  
 Pour plus d’informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Utilisation de modèles pour créer des Extensions de l’éditeur  
 Vous pouvez utiliser des modèles de l’éditeur pour créer des extensions MEF personnaliser classifieurs, motifs et les marges. Il existe des modèles de projets c# et Visual Basic. Pour plus d’informations, consultez [création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 Vous pouvez également utiliser le modèle de projet VSIX pour créer des extensions. Ce modèle fournit uniquement les éléments qui sont requises pour déployer tout type d’extension et inclure le fichier source.extension.vsixmanifest, les références d’assembly requises et un fichier projet qui inclut les tâches de génération qui vous permettent de déployer le extension. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).  
  
 Vous pouvez également créer éditeur composants MEF à partir d’une extension de Package Visual Studio. Les procédures suivantes pour plus d’informations, consultez :  
  
-   [Procédure pas à pas : Utilisation d’une commande Shell avec une extension de l’éditeur](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Procédure pas à pas : Utilisation d’une touche de raccourci avec une extension de l’éditeur](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)