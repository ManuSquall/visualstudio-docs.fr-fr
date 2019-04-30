---
title: 'Procédure : Déboguer XAML avec Workflow Designer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0b8ed6bbb41b2fa3f54d825a13c16b064d010012
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444199"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Procédure : Déboguer du code XAML à l’aide du concepteur de workflow
Les workflows sont définis en code XAML. La représentation de l’interface utilisateur du workflow est construite sur l’arborescence XAML définissant le workflow. L'expérience de débogage est semblable au débogage de workflows dans [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Par exemple, lors du débogage de code XAML, la fenêtre des variables locales, la fenêtre Espion et la fenêtre des threads fonctionnent de la même façon que dans le débogage [!INCLUDE[wfd2](../includes/wfd2-md.md)]. De plus, la vue de la pile des appels pendant le débogage de code XAML est une vue hiérarchique basée sur les lignes du flux d'exécution pour le workflow.  
  
> [!NOTE]
> Si le code XAML pour un workflow se trouve dans le même assembly que les activités, la partie d'assembly des noms de classe n'est pas incluse. Sans cette partie des noms de classe (activité), le code XAML ne peut pas être chargé au moment de l'exécution. Il n'est pas recommandé de définir des activités dans le même espace de noms que le projet principal ; sinon, le code XAML doit être modifié manuellement après avoir été modifié dans le concepteur.  
  
### <a name="to-debug-workflow-xaml"></a>Pour déboguer le code XAML du workflow  
  
1. Ouvrez un workflow ou un projet d'activité dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2. Définir un point d’arrêt sur l’activité ou les activités que vous souhaitez déboguer, comme décrit dans [Comment : Définir des points d’arrêt dans les Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md).  
  
3. Cliquez sur le fichier .xaml qui contient votre définition de flux de travail, puis sélectionnez **afficher le Code**. Vous verrez un point d'arrêt affiché sur la même ligne que la déclaration d'élément XAML de l'activité sur laquelle vous définissez le point d'arrêt en mode Design.  
  
4. Appelez le débogueur, comme décrit dans [Comment : Appelez le débogueur de flux de travail](../workflow-designer/how-to-invoke-the-workflow-debugger.md).  
  
5. Lorsque l'exécution du code atteint l'un de vos points d'arrêt, l'élément XAML associé à ce point d'arrêt est mis en surbrillance. Pour déplacer le point d’arrêt suivant, utilisez le **F10** ou **F11** clé.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Définir des points d’arrêt dans les Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Guide pratique pour appeler le débogueur de workflow](../workflow-designer/how-to-invoke-the-workflow-debugger.md)