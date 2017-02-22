---
title: "Proc&#233;dure&#160;: appeler le d&#233;bogueur de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Proc&#233;dure&#160;: appeler le d&#233;bogueur de workflow
En général, vous déboguez des workflows comme vous déboguez des programmes écrits dans d'autres langages de programmation Visual Studio.Vous pouvez démarrer le débogueur de workflow de plusieurs façons :  
  
-   Sélectionnez **Attacher au processus** dans le menu **Débogage** pour sélectionner le processus hôte en cours d'exécution pour votre instance de workflow.Cette procédure est identique à l'attachement à un processus hôte dans du code managé.  
  
-   Appuyez sur **F5** pour commencer à exécuter une instance du workflow, ou pour continuer l'exécution après qu'un point d'arrêt a été atteint.  
  
-   Utilisez le débogage distant.Pour plus d'informations sur l'utilisation du débogage à distance, consultez [Procédure : activer le débogage à distance](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  Si l'application de workflow cible l'architecture x86 et est hébergée sur un ordinateur qui exécute un système d'exploitation 64 bits, le débogage à distance ne fonctionnera pas à moins que [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ne soit installé sur l'ordinateur distant ou la cible de l'application de workflow soit remplacée par **Any CPU**.  
  
### Exécution du code pas à pas  
  
-   **Pas à pas détaillé** : vous pouvez exécuter une commande de pas à pas détaillé dans une activité à l'aide de la touche **F11**.Le débogueur exécute une commande pas à pas dans le gestionnaire défini.Si aucun gestionnaire n'est défini, vous effectuez as à pas principal sur l'activité ; pour les activités composites, qui contiennent d'autres activités, vous effectuez un pas à pas dans l'activité exécutée en premier.  
  
-   **Pas à pas sortant** : vous pouvez exécuter une commande de pas à pas sortant pour une activité, à l'aide de la combinaison de touches **Maj \+ F11**.La commande de pas à pas sortant permet d'exécuter totalement l'activité en cours et toutes ses activités sœurs.Le débogueur marque ensuite un arrêt sur le parent de l'activité en cours.Lorsque la commande de pas à pas sortant est exécutée à partir d'un gestionnaire de code, le débogueur marque un arrêt sur l'activité à laquelle le gestionnaire est associé.  
  
-   **Pas à pas principal** : vous pouvez exécuter une commande de pas à pas principal à l'aide de la touche **F10**.Lorsque vous effectuez un pas à pas sur une activité composite, le débogueur marque un arrêt sur le premier enfant exécutable de l'activité composite.Lorsque vous effectuez un pas à pas sur une activité non composite \(sur une activité <xref:System.Activities.Statements.Assign>, par exemple\), le débogueur exécute l'activité et ses gestionnaires associés, et marque un arrêt sur l'activité suivante.Si l'activité exécutée est la dernière activité enfant d'une activité composite, après l'exécution, le débogueur marque un arrêt sur l'activité parente.  
  
### Débogage avec la touche F5  
  
-   Si vous générez un projet Application console de workflow, appuyez simplement sur **F5** pour commencer le débogage dans votre application et workflow.Si vous générez une bibliothèque d'activités seule, vous devez posséder une application hôte exécutable comme projet de démarrage.Pour définir un projet de démarrage dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de l'hôte, puis sélectionnez **Définir comme projet de démarrage**.  
  
## Voir aussi  
 [Procédure : définir des points d'arrêt dans les workflows](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md)   
 [Débogage de workflows avec Workflow Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)