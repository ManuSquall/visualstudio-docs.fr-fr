---
title: "Proc&#233;dure pas &#224; pas&#160;: &#233;tendre les VSPackages g&#233;r&#233;s avec l’automatisation | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages gérés, étendre l’automatisation"
  - "automatisation (Visual Studio SDK), procédures pas à pas"
  - "automatisation (Visual Studio SDK), VSPackages managés"
ms.assetid: 7fd2000b-8ec3-4d83-b169-d38008fb57ee
caps.latest.revision: 35
caps.handback.revision: 35
manager: "douge"
---
# Proc&#233;dure pas &#224; pas&#160;: &#233;tendre les VSPackages g&#233;r&#233;s avec l’automatisation
Cette procédure pas à pas montre comment utiliser l’automatisation pour créer un VSPackage managé qui manipule l’environnement de développement intégré \(IDE\) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans cette procédure, vous créez un exemple de VSPackage géré, puis utilisez des méthodes d’automatisation dans le VSPackage résultant pour afficher les propriétés [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans la fenêtre **Sortie**.  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel \(SDK\) Visual Studio. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Emplacements du modèle de projet de package Visual Studio  
 Le modèle de projet de package Visual Studio se trouve à trois emplacements différents dans la boîte de dialogue **Nouveau projet** :  
  
1.  Sous Extensibilité Visual Basic. Le langage par défaut du projet est Visual Basic.  
  
2.  Sous Extensibilité C\#. Le langage par défaut du projet est C\#.  
  
3.  Sous Extensibilité d’autres types de projets. Le langage par défaut du projet est C\+\+.  
  
### Pour créer un VSPackage géré  
  
1.  Créez un projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Package nommé `Auto`.  
  
     Pour plus d’informations sur la création d’un VSPackage géré, consultez [Procédure pas à pas : création d’une commande de menu à l’aide du modèle de package Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  Dans la page **Sélectionner un langage de programmation**, définissez la langue sur [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
3.  Conservez les valeurs par défaut dans la page **Informations de base sur le package Visual Studio**.  
  
4.  Dans la page **Sélectionner les options de package Visual Studio**, cochez la case **Commande de menu**.  
  
5.  Dans la page **Options de commande**, remplacez le **Nom de commande** par `Auto`.  
  
6.  Cliquez sur le bouton **Terminer**.  
  
     Le modèle génère un projet géré nommé Auto.  
  
7.  Générez la solution et vérifiez qu’elle est compilée sans erreur.  
  
### Pour appeler le modèle Automation  
  
1.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet Auto, puis cliquez sur **Ajouter**, **Référence**.  
  
2.  Dans l’onglet **.NET** de la boîte de dialogue **Référence**, double\-cliquez sur **EnvDTE**.  
  
     Vous ajoutez ainsi une référence à l’espace de noms Automation EnvDTE.  
  
3.  Dans le fichier AutoPackage, ajoutez la référence d’espace de noms suivante.  
  
     [!code-cs[VSSDKAuto#1](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_1.cs)]
     [!code-vb[VSSDKAuto#1](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_1.vb)]  
  
4.  Dans le fichier AutoPackage, remplacez le corps de la méthode `MenuItemCallback` par les lignes suivantes :  
  
     [!code-cs[VSSDKAuto#2](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_2.cs)]
     [!code-vb[VSSDKAuto#2](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_2.vb)]  
  
 Ce code appelle <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> pour obtenir un objet Automation <xref:EnvDTE.DTE> qui représente l’IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Le code d’automatisation de `MenuItemCallback` crée un volet dans la fenêtre **Sortie** nommé **Test**. Le nom et la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sont ensuite écrits dans le nouveau volet **Sortie**.  
  
1.  Créez et démarrez le projet Auto en mode débogage en appuyant sur F5.  
  
     La build expérimentale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp\) est alors démarrée.  
  
    > [!NOTE]
    >  Les deux versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sont ouvertes à ce stade.  
  
2.  Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp, dans le menu **Outils**, cliquez sur **Auto**.  
  
     Un nouveau volet nommé **Test** s’ouvre dans la fenêtre **Sortie** et affiche ce qui suit :  
  
    ```  
    Name is Microsoft Visual Studio Version is x.xx  
    ```  
  
     Où x.xx correspond au numéro de version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] le plus récent.  
  
     Pour plus d’informations sur les exemples d’automatisation, consultez [Automation Samples for Visual Studio](http://www.microsoft.com/downloads/details.aspx?familyid=3ff9c915-30e5-430e-95b3-621dccd25150&displaylang=en).  
  
## Voir aussi  
 [Extension de l'environnement Visual Studio](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)