---
title: 'Procédure : Configurer des projets et cibler des plateformes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ee35a42ea28295869fe05bf6cd1d2c49f12cc39b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791408"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Procédure : Configurer des projets pour des plateformes cibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vous permet de configurer vos applications pour cibler différentes plateformes (y compris des plateformes 64 bits). Pour plus d’informations sur la prise en charge des plateformes 64 bits dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], consultez [Applications 64 bits](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>Ciblage de plateformes avec le Gestionnaire de configurations  
 Le **Gestionnaire de configurations** vous permet d’ajouter rapidement une nouvelle plateforme à cibler avec votre projet. Si vous sélectionnez l'une des plateformes incluses avec [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], les propriétés de votre projet sont modifiées afin de générer votre projet pour la plateforme sélectionnée.  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Pour configurer un projet pour cibler une plateforme 64 bits  
  
1. Dans la barre de menus, choisissez **Générer**, puis **Gestionnaire de configurations**.  
  
2. Dans la liste **Plateforme de la solution active**, choisissez une plateforme 64 bits pour la solution à cibler, puis choisissez le bouton **Fermer**.  
  
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
  
-   Pour les projets [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], consultez [/platform (Visual Basic)](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).  
  
-   Pour les projets [!INCLUDE[csprcs](../includes/csprcs-md.md)], consultez [Générer, page du Concepteur de projet (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
-   Pour les projets [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], consultez [/clr (Compilation pour le Common Language Runtime)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des plateformes de générations](../ide/understanding-build-platforms.md)   
 [/platform (Options du compilateur C#)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04)   
 [Applications 64 bits](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Prise en charge de l’IDE de Visual Studio 64 bits](../ide/visual-studio-ide-64-bit-support.md)
