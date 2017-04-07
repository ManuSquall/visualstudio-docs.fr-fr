---
title: "Guide pratique pour configurer des projets afin de cibler des plateformes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: c9ab9bf094a57baf4a309e3064cfcea9180dfebc
ms.lasthandoff: 04/05/2017

---
# <a name="how-to-configure-projects-to-target-platforms"></a>Guide pratique pour configurer des projets afin de cibler des plateformes
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous permet de configurer vos applications pour cibler différentes plateformes (y compris des plateformes 64 bits). Pour plus d’informations sur la prise en charge des plateformes 64 bits dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consultez [Applications 64 bits](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>Ciblage de plateformes avec le Gestionnaire de configurations  
 Le **Gestionnaire de configurations** vous permet d’ajouter rapidement une nouvelle plateforme à cibler avec votre projet. Si vous sélectionnez l'une des plateformes incluses avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], les propriétés de votre projet sont modifiées afin de générer votre projet pour la plateforme sélectionnée.  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Pour configurer un projet pour cibler une plateforme 64 bits  
  
1.  Dans la barre de menus, choisissez **Générer**, puis **Gestionnaire de configurations**.  
  
2.  Dans la liste **Plateforme de la solution active**, choisissez une plateforme 64 bits pour la solution à cibler, puis choisissez le bouton **Fermer**.  
  
    1.  Si la plateforme voulue ne s’affiche pas dans la liste **Plateforme de la solution active**, choisissez **Nouveau**.  
  
         La boîte de dialogue **Nouvelle plateforme de solution** s’affiche.  
  
    2.  Dans la liste **Tapez ou sélectionnez la nouvelle plateforme**, choisissez **x64**.  
  
        > [!NOTE]
        >  Si vous affectez un nouveau nom à votre configuration, vous devrez peut-être modifier les paramètres dans le **Concepteur de projet** pour cibler la plateforme correcte.  
  
    3.  Si vous souhaitez copier les paramètres d’une configuration de plateforme actuelle, choisissez-la, puis choisissez le bouton **OK**.  
  
 Les propriétés de tous les projets qui ciblent la plateforme 64 bits sont mises à jour et la prochaine génération du projet est optimisée pour les plateformes 64 bits.  
  
## <a name="targeting-platforms-in-the-project-designer"></a>Ciblage de plateformes dans le Concepteur de projets  
 Le Concepteur de projets permet également de cibler différentes plateformes avec votre projet. Si la sélection de l’une des plateformes incluses dans la liste affichée dans la boîte de dialogue **Nouvelle plateforme de solution** ne fonctionne pas pour votre solution, vous pouvez créer un nom de configuration personnalisée, puis en modifier les paramètres dans le **Concepteur de projet** pour cibler la plateforme appropriée.  
  
 L’exécution de cette tâche varie suivant le langage de programmation que vous utilisez. Pour plus d'informations, consultez les liens suivants :   
  
-   Pour les projets [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], consultez [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
-   Pour les projets [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], consultez [Générer, page du Concepteur de projet (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
-   Pour les projets [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], consultez [/clr (Compilation pour le Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des plateformes de générations](../ide/understanding-build-platforms.md)   
 [/platform (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)   
 [Applications 64 bits](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Prise en charge de l’IDE de Visual Studio 64 bits](../ide/visual-studio-ide-64-bit-support.md)
