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
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 3cc009e23d123f50b108533e135bd51e123b3809
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Prise en main de Service de langage et les Extensions de l’éditeur
Vous pouvez utiliser des extensions de l’éditeur pour ajouter des fonctionnalités de service de langage telles que le mode plan, accolades correspondantes, IntelliSense et les ampoules à votre propre langage de programmation ou à n’importe quel type de contenu. Vous pouvez également personnaliser l’apparence et le comportement de l’éditeur Visual Studio, par exemple texte coloration, marges, motifs et autres éléments visuels. Vous pouvez également définir votre propre type de contenu et spécifier l’apparence et le comportement des affichages de texte dans laquelle votre contenu s’affiche.  
  
 Pour commencer à écrire des extensions de l’éditeur, utilisez les modèles de projet d’éditeur qui sont installés dans le cadre du SDK Visual Studio. Le Kit de développement Visual Studio est un ensemble d’outils qui facilitent le développement d’extensions Visual Studio, à l’aide de packages VS ou à l’aide de Managed Extensibility Framework (MEF) téléchargeable.  
  
> [!NOTE]
>  Pour plus d’informations sur le Kit de développement Visual Studio, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 Nous recommandons que vous en savoir plus sur les concepts suivants et les technologies avant d’écrire vos propres extensions de l’éditeur.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) et les Extensions de l’éditeur  
 L’interface Visual Studio editor (UI) est implémentée à l’aide de Windows Presentation Foundation (WPF). WPF fournit une expérience visuelle riche et un modèle de programmation cohérent qui sépare les aspects visuels du code de la logique métier. Vous pouvez utiliser les nombreuses fonctionnalités et éléments WPF lorsque vous créez des extensions de l’éditeur. Pour plus d’informations, consultez [Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) et les Extensions de l’éditeur  
 L’éditeur Visual Studio utilise Managed Extensibility Framework (MEF) pour gérer les composants et ses extensions. MEF permet également aux développeurs plus de créer facilement des extensions pour une application hôte, tel que Visual Studio. Dans ce cadre, vous définissez une extension en fonction d’un contrat MEF et exportez en tant que composant MEF. L’application hôte gère les composants à les rechercher, enregistrant et à s’assurer qu’ils sont appliqués au contexte correct.  
  
> [!NOTE]
>  Pour plus d’informations sur MEF dans l’éditeur, consultez [Managed Extensibility Framework dans l’éditeur](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Points d’Extension de l’éditeur Visual Studio et des Extensions  
 Éditeur des points d’extension sont des composants MEF que vous pouvez personnaliser et étendre. Dans certains cas, vous étendez le point d’extension en implémentant une interface et en exportant ainsi que les métadonnées correctes. Dans d’autres cas vous déclarez une extension et l’exporter dans un type particulier.  
  
 Voici quelques-uns des types d’extensions de l’éditeur de base :  
  
-   Marges et des barres de défilement  
  
-   Balises  
  
-   Ornements  
  
-   Options  
  
-   IntelliSense  
  
 Pour plus d’informations sur les points d’extension de l’éditeur, consultez [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Déploiement d’Extensions de l’éditeur  
 Dans Visual Studio, vous déployez des extensions de l’éditeur en lui ajoutant un fichier de métadonnées nommé source.extension.vsixmanifest à la solution, la génération de la solution et ensuite une copie des fichiers binaires et le manifeste dans un dossier connu vers Visual Studio. Le fichier manifest définit les faits de base sur l’extension (par exemple, nom, auteur, version et type de contenu). Pour plus d’informations sur le fichier de manifeste VSIX et comment déployer des extensions, consultez [de livraison d’Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Lorsque vous installez une extension sur un ordinateur, inclure les fichiers binaires et le manifeste dans un sous-dossier du dossier connu pour Visual Studio.  
  
> [!WARNING]
>  Vous n’avez pas à vous soucier des détails des manifestes et emplacements de déploiement si vous utilisez un des modèles d’extensibilité éditeur qui sont inclus dans Visual Studio. Les modèles contiennent tout ce qui est requis pour enregistrer et déployer une extension.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Extensions dans l’Instance expérimentale en cours d’exécution  
 Vous pouvez isoler votre version de travail de Visual Studio lorsque vous développez une extension en le déployant dans le dossier suivant expérimental (sur Windows Vista et Windows 7) :  
  
 *%LocalAppData%*\VisualStudio\10.0Exp\Extensions\\*société*\\*ExtensionID*  
  
 où *% LocalAppData%* est le nom de l’utilisateur ayant ouvert une session, *société* est le nom de la société qui possède l’extension, et *ExtensionID* est l’ID de l’extension.  
  
 Lorsque vous déployez une extension à l’emplacement expérimentale, il s’exécute en mode débogage. Une deuxième instance de Visual Studio est démarrée et se nomme **Microsoft Visual Studio - Instance expérimentale**.  
  
## <a name="managing-extensions"></a>Gestion des extensions  
 Extensions pour Visual Studio sont répertoriées dans **Extensions et mises à jour** (sur le **outils** menu). Si vous testez une extension dans l’instance expérimentale, il est répertorié dans **Extensions et mises à jour** dans l’instance expérimentale, mais n’est ne pas répertorié dans l’instance de développement.  
  
 Pour plus d’informations, consultez [recherche et utilisation d’Extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Utilisation de modèles pour créer des Extensions de l’éditeur  
 Vous pouvez utiliser les modèles d’éditeurs pour créer des extensions MEF qui personnalisent les classifieurs, motifs et les marges. Il existe des modèles pour les projets c# et Visual Basic. Pour plus d’informations, consultez [avec un éditeur de modèle d’élément pour créer une Extension](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 Vous pouvez également utiliser le modèle de projet VSIX pour créer des extensions. Ce modèle fournit uniquement les éléments qui sont requis pour déployer tout type d’extension et incluent le fichier source.extension.vsixmanifest, les références d’assembly nécessaires et un fichier de projet qui inclut les tâches de génération qui vous permettent de déployer l’extension. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).  
  
 Vous pouvez également créer l’éditeur composants MEF à partir d’une extension de Package Visual Studio. Les procédures suivantes pour plus d’informations, consultez :  
  
-   [Procédure pas à pas : Utilisant une invite de commandes avec une Extension de l’éditeur](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Procédure pas à pas : L’utilisation d’une touche de raccourci avec une Extension de l’éditeur](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md)
