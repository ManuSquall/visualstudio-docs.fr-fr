---
title: "Appel du d&#233;bogueur Visual Studio pour Windows Workflow Foundation (h&#233;rit&#233;) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "débogueur, workflow"
  - "débogage de workflows, lancer le débogueur"
  - "débogage, utiliser le débogueur de workflow"
  - "commande pas à pas détaillé"
  - "commande pas à pas sortant"
  - "commande pas à pas principal"
  - "pas à pas"
  - "pas à pas, commandes"
  - "débogueur de workflows, démarrer"
  - "workflows, débogueur"
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Appel du d&#233;bogueur Visual Studio pour Windows Workflow Foundation (h&#233;rit&#233;)
Cette rubrique décrit comment utiliser le débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour déboguer des applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] dans le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité.Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 En général, vous déboguez les workflows hérités comme vous déboguez des programmes écrits dans d'autres langages de programmation Visual Studio.Vous pouvez démarrer le débogueur [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] pour Windows Workflow Foundation comme suit :  
  
-   Sélectionnez **Attacher au processus** dans le menu **Débogage** pour sélectionner, parmi les processus disponibles, une instance de workflow en cours d'exécution.  
  
-   Appuyez sur **F5** pour commencer à exécuter une instance du workflow, ou pour continuer l'exécution après qu'un point d'arrêt a été atteint.  
  
## Exécution pas à pas du code  
 Le débogueur prend en charge l'une des procédures de débogage les plus courantes : l'exécution pas à pas, qui consiste à exécuter le code ligne par ligne.Il existe trois commandes d'exécution pas à pas du code :  
  
-   **Pas à pas détaillé** : vous pouvez exécuter une commande de pas à pas détaillé dans une activité à l'aide de la touche **F11**.Le débogueur exécute une commande pas à pas dans le gestionnaire défini.Si aucun gestionnaire n'est défini, vous passez outre l'activité ; pour les activités composites qui contiennent d'autres activités, vous effectuez un pas à pas dans l'activité exécutée en premier.L'exécution d'une commande pas à pas dans des gestionnaires de code à partir du concepteur n'est pas prise en charge pour les activités suivantes : **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**ou **ReplicatorActivity**.Pour déboguer les gestionnaires associés à ces activités, vous devez placer des points d'arrêt explicites dans le code.  
  
-   **Pas à pas sortant** : vous pouvez exécuter une commande de pas à pas sortant pour une activité, à l'aide de la combinaison de touches **Shift\-F11**.La commande de pas à pas sortant permet d'exécuter totalement l'activité en cours et toutes ses activités frères.Le débogueur marque ensuite un arrêt sur le parent de l'activité en cours.Lorsque la commande de pas à pas sortant est exécutée à partir d'un gestionnaire de code, le débogueur marque un arrêt sur l'activité à laquelle le gestionnaire est associé.  
  
-   **Pas à pas principal** : vous pouvez exécuter une commande de pas à pas principal à l'aide de la touche **F10**.Lorsque vous effectuez un pas à pas sur une activité composite.le débogueur s'arrête sur le premier enfant exécutable de l'activité composite.Lorsque vous effectuez un pas à pas sur une activité non composite \(sur une activité **CodeActivity**, par exemple\), le débogueur exécute l'activité et ses gestionnaires associés, et marque un arrêt sur l'activité suivante.Si l'activité exécutée est la dernière activité enfant d'une activité composite, après l'exécution, le débogueur marque un arrêt sur l'activité parente.  
  
## Attachement à un processus  
 Pour déboguer un workflow en effectuant un attachement à un processus, sélectionnez le processus disponible dans la zone de liste **Processus disponibles**, dans la boîte de dialogue **Attacher au processus**.Si **Automatique : Code de workflow** n'est pas affiché dans la zone de texte **Attacher au processus**, cliquez sur **Sélectionner**.Dans la boîte de dialogue **Sélectionner le type de code**, cliquez sur **Déboguer ces types de codes** et sélectionnez **Workflow**.Cliquez ensuite sur **OK**, puis sur **Attacher**.  
  
## Débogage avec la touche F5  
 Si une application hôte de workflow et une DLL de workflow se trouvent dans des projets Visual Studio différents \(lorsque vous utilisez une bibliothèque d'activité de workflow, par exemple\), vous devez placer le projet de DLL de workflow en projet de démarrage de la solution Visual Studio ; cela permet de déboguer le workflow à l'aide de la touche **F5**.Vous devez également définir le chemin d'accès à l'application hôte dans la propriété **Démarrer le programme externe** du projet de DLL de workflow.  
  
 Pour définir un projet de démarrage dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis sélectionnez **Définir comme projet de démarrage**.Pour définir le chemin d'accès à l'hôte dans la propriété **Démarrer le programme externe**, double\-cliquez sur le nœud **Propriétés** du projet de workflow dans l'Explorateur de solutions, puis cliquez sur l'onglet **Débogage**.Dans **Action de démarrage**, sélectionnez **Démarrer le programme externe** et entrez le chemin d'accès au fichier .exe qui héberge le workflow que vous souhaitez déboguer.  
  
 Si l'application hôte est définie comme projet de démarrage, seul le débogueur Visual Studio est appelé pour déboguer \(le débogueur [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] pour Windows Workflow Foundation n'est pas appelé\).Si le débogueur Visual Studio est utilisé, seuls les points d'arrêt de code C\# ou Visual Basic sont atteints ; les points d'arrêt définis dans le concepteur de workflow ne sont pas atteints.Par exemple, un point d'arrêt défini sur une activité <xref:System.Workflow.Activities.ParallelActivity> dans le concepteur est atteint si le débogueur [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] pour Windows Workflow Foundation est utilisé, mais ne l'est pas lorsque vous utilisez le débogueur Visual Studio.  
  
## Voir aussi  
 [Procédure : définir des points d'arrêt dans les workflows \(héritée\)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Débogage de workflows hérités](../workflow-designer/debugging-legacy-workflows.md)