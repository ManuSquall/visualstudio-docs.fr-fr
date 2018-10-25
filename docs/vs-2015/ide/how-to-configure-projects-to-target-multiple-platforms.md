---
title: Guide pratique pour configurer des projets pour plusieurs plateformes cibles | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9a3010e6304124ee306c5ecad3593df98d555523
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921832"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Comment : configurer des projets pour plusieurs plateformes cibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permet à une solution de cibler en même temps plusieurs architectures, ou plateformes, de processeur différentes. Les propriétés permettant de les définir sont accessibles à l’aide de la boîte de dialogue **Gestionnaire de configurations**.  
  
## <a name="targeting-a-platform"></a>Ciblage d’une plateforme  
 La boîte de dialogue **Gestionnaire de configurations** vous permet de créer et de définir des plateformes et des configurations au niveau de la solution et au niveau du projet. Un ensemble unique de propriétés peut être associé à chaque combinaison de configurations au niveau de la solution et de cibles, ce qui vous permet de basculer facilement entre, par exemple, une configuration Release qui cible une plateforme [!INCLUDE[vcprx64](../includes/vcprx64-md.md)], une configuration Release qui cible une plateforme x86 et une configuration Debug qui cible une plateforme x86.  
  
#### <a name="to-set-your-configuration-to-target-a-different-platform"></a>Pour définir votre configuration afin de cibler une plateforme différente  
  
1.  Dans le menu **Générer**, cliquez sur **Gestionnaire de configuration**.  
  
2.  Dans la **zone Plateforme de la solution active**, sélectionnez la plateforme que votre solution doit cibler, ou sélectionnez **\<Nouveau>** pour créer une nouvelle plateforme. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] compile votre application de façon à cibler la plateforme qui est définie comme plateforme active dans la boîte de dialogue **Gestionnaire de configurations**.  
  
## <a name="removing-a-platform"></a>Suppression d’une plateforme  
 Si vous constatez que vous n’avez pas besoin d’une plateforme, vous pouvez la supprimer à l’aide de la boîte de dialogue Gestionnaire de configurations. Cela supprime tous les paramètres de solution et de projet que vous avez configurés pour cette combinaison de configuration et de cible.  
  
#### <a name="to-remove-a-platform"></a>Pour supprimer une plateforme  
  
1.  Dans le menu **Générer**, cliquez sur **Gestionnaire de configuration**.  
  
2.  Dans la **zone Plateforme de la solution active**, sélectionnez **\<Modifier>**. La boîte de dialogue **Modifier les plateformes de solution** s’affiche.  
  
3.  Cliquez sur la plateforme à supprimer, puis sur **Supprimer**.  
  
## <a name="targeting-multiple-platforms-with-one-solution"></a>Ciblage de plusieurs plateformes avec une seule solution  
 Étant donné que vous pouvez changer les paramètres en fonction de la combinaison de paramètres de configuration et de plateforme, vous pouvez configurer une solution capable de cibler plusieurs plateformes.  
  
#### <a name="to-target-multiple-platforms"></a>Pour cibler plusieurs plateformes  
  
1.  Utilisez le **Gestionnaire de configurations** pour ajouter au moins deux plateformes pour la solution.  
  
2.  Sélectionnez la plateforme que vous voulez cibler dans la liste **Plateforme de la solution active**.  
  
3.  Générez la solution.  
  
#### <a name="to-build-multiple-solution-configurations-at-once"></a>Pour générer plusieurs configurations de solution à la fois  
  
1. Utilisez le **Gestionnaire de configurations** pour ajouter au moins deux plateformes pour la solution.  
  
2. Utilisez la fenêtre **Générer en tâche de fond** pour générer plusieurs configurations de solution à la fois.  
  
   Il est possible d’avoir une plateforme au niveau de la solution définie, par exemple, sur [!INCLUDE[vcprx64](../includes/vcprx64-md.md)], et de n’avoir, dans cette solution, aucun projet ciblant cette même plateforme. Il est également possible d’avoir plusieurs projets dans votre solution, chacun ciblant une plateforme différente. Si vous êtes dans l’une ou l’autre de ces situations, il est recommandé de créer une nouvelle configuration portant un nom descriptif afin d’éviter toute confusion.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)   
 [Présentation des configurations de build](../ide/understanding-build-configurations.md)   
 [Génération et nettoyage de solutions et de projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)



