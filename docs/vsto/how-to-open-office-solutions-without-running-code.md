---
title: "Comment&#160;: ouvrir des solutions Office sans ex&#233;cuter le code | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "assemblys (développement Office dans Visual Studio), ignorer"
  - "ignorer des assemblys"
  - "documents (développement Office dans Visual Studio), ouvrir sans exécuter du code"
  - "documents Office (développement Office dans Visual Studio), ouvrir sans exécuter du code"
  - "solutions Office (développement Office dans Visual Studio), ouvrir"
  - "ouvrir des solutions Office"
  - "solutions (développement Office dans Visual Studio), ouvrir"
ms.assetid: a853d91c-9fd6-421a-b3a2-956b6b494b96
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: ouvrir des solutions Office sans ex&#233;cuter le code
  Une solution Microsoft Office créée avec des extensions de code managé s'exécute même si le paramètre de sécurité défini dans l'application Office de l'utilisateur final a la valeur Élevé.  Cela s'explique par le fait que la sécurité du code d'assembly .NET est gérée par le Microsoft .NET Framework, et non par Microsoft Office.  
  
 Il peut toutefois arriver que vous souhaitiez ouvrir un document sans exécuter le code.  Par exemple, le code qui s'exécute à l'ouverture du document peut en modifier le contenu alors que vous souhaitez mettre à jour l'apparence du document avant que le code ne le modifie.  Ou bien, vous pouvez souhaiter envoyer à un destinataire le document contenant certaines informations et empêcher l'exécution du code susceptible de modifier son contenu.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Il existe plusieurs manières d'ouvrir un document ou un classeur qui contient des extensions de code managé, sans exécuter le code assembleur.  
  
### Pour ignorer l'assembly à l'aide de la touche MAJ  
  
-   Ouvrez les documents et classeurs dans le menu **Fichier** en maintenant la touche MAJ enfoncée pour empêcher Word et Excel de déclencher des événements d'initialisation au cours de l'ouverture des documents.  
  
    > [!NOTE]  
    >  Si vous ouvrez un document ou un classeur à partir du volet de tâches **Mise en route**, le fait de maintenir la touche MAJ enfoncée n'ignore pas le code.  Par ailleurs, maintenir la touche MAJ enfoncée n'empêche pas le déclenchement des événements après l'ouverture du document.  
  
     Cette méthode est utile si vous souhaitez ouvrir un document pour le mettre à jour sans que le code ne s'exécute et ne modifie le document au préalable.  
  
### Pour ignorer un assembly en le renommant ou en le supprimant  
  
-   Si vous disposez des autorisations appropriées sur l'ordinateur où se trouve l'assembly, vous pouvez renommer ou supprimer ce dernier de sorte que le document ou classeur ne puisse pas le rechercher.  Cette procédure entraîne le déclenchement d'une erreur à chaque ouverture du document Office.  
  
     Si la solution est utilisée par plusieurs personnes, cette méthode interdit à quiconque de l'exécuter.  Cette restriction peut être utile si un problème est relevé dans le code ou un serveur référencé et que vous voulez empêcher tous les utilisateurs de l'exécuter.  
  
## Voir aussi  
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifestes d'application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  