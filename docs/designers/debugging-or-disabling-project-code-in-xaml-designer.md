---
title: "Débogage ou désactivation de code de projet dans le concepteur XAML | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 138f318b84044a1ed8a92f9b2ee7b47b2211cdb7
ms.lasthandoff: 02/22/2017

---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>Débogage ou désactivation de code de projet dans le concepteur XAML
Dans bien des cas, les exceptions non gérées dans le concepteur XAML peuvent être provoquées par le code de projet, qui tente d’accéder à des propriétés ou méthodes qui retournent des valeurs différentes ou qui fonctionnent de manière différente quand votre application s’exécute dans le concepteur. Vous pouvez résoudre ces exceptions en déboguant le code du projet dans une autre instance de Visual Studio, voire les éviter temporairement en désactivant le code de projet dans le concepteur.  
  
 Le code de projet est constitué des éléments suivants :  
  
-   Contrôles personnalisés et contrôles utilisateur  
  
-   Bibliothèques de classes  
  
-   Convertisseurs de valeurs  
  
-   Liaisons avec des données au moment de la conception générées à partir du code de projet  
  
 Quand le code de projet est désactivé, Visual Studio affiche des espaces réservés. Pour une liaison, il peut s’agir du nom de la propriété dans le cas où les données ne sont plus disponibles ou bien un espace réservé pour un contrôle qui n’est plus en cours d’exécution.  
  
 ![Boîte de dialogue d’exception non gérée](~/docs/designers/media/xaml_unhandledexception.png "XAML_UnhandledException")  
  
#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>Pour déterminer si le code de projet est à l’origine d’une exception  
  
1.  Dans la boîte de dialogue de l’exception non gérée, choisissez le lien **Cliquez ici pour recharger le concepteur** .  
  
2.  Dans la barre de menus, choisissez **Déboguer**, **Démarrer le débogage** pour générer et exécuter l’application.  
  
     Si l’application se génère et s’exécute correctement, l’exception au moment de la conception est peut-être due à votre code de projet s’exécutant dans le concepteur.  
  
#### <a name="to-debug-project-code-running-in-the-designer"></a>Pour déboguer le code de projet s’exécutant dans le concepteur  
  
1.  Dans la boîte de dialogue de l’exception non gérée, choisissez le lien **Cliquez ici pour désactiver l’exécution du code de projet et recharger le concepteur** .  
  
2.  Dans le Gestionnaire des tâches Windows, cliquez sur le bouton **Fin de tâche** pour fermer toutes les instances du concepteur XAML Visual Studio en cours d’exécution.  
  
     ![Instances du concepteur XAML dans TaskManager](~/docs/designers/media/xaml_taskmanager.png "XAML_TaskManager")  
  
3.  Dans Visual Studio, ouvrez la page XAML qui contient le code ou le contrôle à déboguer.  
  
4.  Ouvrez une nouvelle instance de Visual Studio, puis ouvrez une deuxième instance de votre projet.  
  
5.  Définissez un point d’arrêt dans votre code de projet.  
  
6.  Dans la nouvelle instance de Visual Studio, dans la barre de menus, choisissez **Déboguer**, **Attacher au processus**.  
  
7.  Dans la boîte de dialogue **Attacher au processus** , dans la liste **Processus disponibles** , choisissez **XDesProc.exe**, puis cliquez sur le bouton **Attacher** .  
  
     ![Processus du concepteur XAML](~/docs/designers/media/xaml_attach.png "XAML_Attach")  
  
     Il s’agit ici du processus destiné au concepteur XAML de la première instance de Visual Studio.  
  
8.  Dans la première instance de Visual Studio, dans la barre de menus, choisissez **Déboguer**, **Démarrer le débogage**.  
  
     Vous pouvez maintenant parcourir pas à pas votre code qui s’exécute dans le concepteur.  
  
#### <a name="to-disable-project-code-in-the-designer"></a>Pour désactiver le code de projet dans le concepteur  
  
-   Dans la boîte de dialogue de l’exception non gérée, choisissez le lien **Cliquez ici pour désactiver l’exécution du code de projet et recharger le concepteur** .  
  
-   Sinon, dans la barre d’outils du concepteur XAML, cliquez sur le bouton **Désactiver le code de projet** .  
  
     ![Le bouton Désactiver le code de projet](~/docs/designers/media/xaml_disablecode.png "XAML_DisableCode")  
  
     Vous pouvez cliquer à nouveau sur le bouton pour réactiver le code de projet.  
  
    > [!NOTE]
    >  Pour les projets qui ciblent des processeurs ARM ou X64, Visual Studio ne peut pas exécuter le code de projet dans le concepteur. De ce fait, le bouton **Désactiver le code de projet** est désactivé dans le concepteur.  
  
-   Les deux options ont pour effet de recharger le concepteur et de désactiver l’ensemble du code du projet associé.  
  
    > [!NOTE]
    >  La désactivation du code de projet peut entraîner une perte de données au moment de la conception. Une autre solution consiste à déboguer le code s’exécutant dans le concepteur.  
  
## <a name="see-also"></a>Voir aussi  
 [Conception XAML dans Visual Studio et Blend pour Visual Studio](../designers/designing-xaml-in-visual-studio.md)
