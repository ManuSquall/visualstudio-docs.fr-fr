---
title: "Proc&#233;dure&#160;: d&#233;boguer du code XAML avec Workflow Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Proc&#233;dure&#160;: d&#233;boguer du code XAML avec Workflow Designer
Les workflows sont définis en code XAML.La représentation de l'interface utilisateur du workflow est construite sur l'arborescence XAML définissant le workflow.L'expérience de débogage est semblable au débogage de workflows dans [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Par exemple, lors du débogage de code XAML, la fenêtre des variables locales, la fenêtre Espion et la fenêtre des threads fonctionnent de la même façon que dans le débogage [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].De plus, la vue de la pile des appels pendant le débogage de code XAML est une vue hiérarchique basée sur les lignes du flux d'exécution pour le workflow.  
  
> [!NOTE]
>  Si le code XAML pour un workflow se trouve dans le même assembly que les activités, la partie d'assembly des noms de classe n'est pas incluse.Sans cette partie des noms de classe \(activité\), le code XAML ne peut pas être chargé au moment de l'exécution.Il n'est pas recommandé de définir des activités dans le même espace de noms que le projet principal ; sinon, le code XAML doit modifié manuellement après avoir été modifié dans le concepteur.  
  
### Pour déboguer le code XAML du workflow  
  
1.  Ouvrez un workflow ou un projet d'activité dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Définissez un point d'arrêt sur l'activité ou les activités que vous voulez déboguer, comme décrit dans la rubrique [Procédure : définir des points d'arrêt dans les workflows](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md).  
  
3.  Cliquez avec le bouton droit sur le fichier .xaml qui contient votre définition de workflow, puis sélectionnez **Afficher le code**.Vous verrez un point d'arrêt affiché sur la même ligne que la déclaration d'élément XAML de l'activité sur laquelle vous définissez le point d'arrêt en mode Design.  
  
4.  Appelez le débogueur, comme décrit dans la rubrique [Procédure : appeler le débogueur de workflow](../workflow-designer/how-to-invoke-the-workflow-debugger.md).  
  
5.  Lorsque l'exécution du code atteint l'un de vos points d'arrêt, l'élément XAML associé à ce point d'arrêt est mis en surbrillance.Pour passer au point d'arrêt suivant, utilisez la touche **F10** ou **F11**.  
  
## Voir aussi  
 [Procédure : définir des points d'arrêt dans les workflows](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md)   
 [Procédure : appeler le débogueur de workflow](../workflow-designer/how-to-invoke-the-workflow-debugger.md)