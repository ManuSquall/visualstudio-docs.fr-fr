---
title: "Vous devez activer explicitement l&#39;acc&#232;s au syst&#232;me de projet Microsoft Office Visual Basic pour Applications avant de pouvoir cr&#233;er ou ouvrir un projet Visual Studio Tools pour Microsoft Office System | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vst.project.vbawrongversion"
  - "VST.Project.VBASecurityGenericError"
  - "VST.Project.VBASecurityPermissions"
  - "VST.SelectDocWizard.MissingCOM"
  - "VST.Project.VBASecurityNotSet"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 538021e6-1776-453d-9899-d7fca2f1f58f
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Vous devez activer explicitement l&#39;acc&#232;s au syst&#232;me de projet Microsoft Office Visual Basic pour Applications avant de pouvoir cr&#233;er ou ouvrir un projet Visual Studio Tools pour Microsoft Office System
  Les projets de développement Office requièrent un accès au système de projet Visual Basic pour Applications dans Microsoft Office Word et Microsoft Office Excel, même s'ils n'utilisent pas Visual Basic pour Applications.  La prise en charge de la conception des contrôles dans les projets Visual Basic et C\# est liée au système de projet Visual Basic pour Applications.  
  
 Certains virus des macros Microsoft Office tentent d'automatiser le système de projet Visual Basic pour Applications dans le but de se propager.  En activant l'accès au système de projet Visual Basic pour Applications, vous supprimez une protection qui empêche les virus des macros de se répandre.  Toutefois, la sécurité normale appliquée aux macros reste en place. Ainsi, le niveau de sécurité des macros et la liste des éditeurs approuvés que vous tenez à jour pour vos applications Office déterminent si une macro s'exécute sur votre ordinateur.  
  
> [!NOTE]  
>  Cela s'applique uniquement à l'ordinateur de développement.  Les ordinateurs des utilisateurs finaux n'ont pas besoin d'activer cette option pour exécuter les solutions Office.  
  
 Il est important de noter que la désactivation de l'accès au système de projet Visual Basic pour Applications ne protège pas en soi contre les virus, elle vous aide simplement à empêcher certains virus de se répandre dans d'autres documents si votre ordinateur est infecté par un virus de macro.  L'option est désactivée par défaut pour apporter une couche supplémentaire de protection à votre ordinateur, mais son activation ne rend pas votre ordinateur plus vulnérable aux virus si vous appliquez les meilleures pratiques en matière de sécurité.  
  
 La meilleure protection contre les virus des macros Office est d'exécuter Office avec un niveau de sécurité défini sur Élevé ou Très élevé, pour ne faire confiance qu'aux macros provenant de sources connues et vérifiées, et pour toujours disposer des derniers correctifs de sécurité et scanners antivirus.  
  
 Pour plus d'informations sur la protection de votre PC contre les virus et autre code malveillant, voir [http:\/\/www.microsoft.com\/protect](http://www.microsoft.com/protect).  
  
 Vous pouvez activer ou désactiver manuellement l'option **Faire confiance au projet Visual Basic**.  
  
 Vous pouvez réparer votre installation Office si des erreurs VBA ou COM s'affichent.  
  
### Pour activer ou désactiver l'accès aux projets Visual Basic  
  
1.  Dans le menu **Outils** de Word ou Excel, pointez sur **Macro**, puis cliquez sur **Sécurité**.  
  
2.  Dans la boîte de dialogue **Sécurité**, cliquez sur l'onglet **Éditeurs approuvés**.  
  
3.  Sélectionnez l'option **Faire confiance au projet Visual Basic** pour l'activer, ou désélectionnez\-la pour la désactiver.  
  
4.  Cliquez sur **OK**.  
  
### Pour définir le niveau de sécurité des macros Office  
  
1.  Dans le menu **Outils** de Word ou Excel, pointez sur **Macro**, puis cliquez sur **Sécurité**.  
  
2.  Sous l'onglet **Niveau de sécurité**, sélectionnez le paramètre souhaité.  
  
     L'onglet **Niveau de sécurité** contient des détails sur chaque niveau.  Pour plus d'informations, voir la rubrique « Niveaux de sécurité des macros » dans l'aide Office.  
  
### Pour installer VBA avec le système Microsoft Office 2007  
  
1.  Dans le Panneau de configuration, exécutez **Ajouter ou supprimer des programmes** ou **Programmes et fonctionnalités**.  
  
2.  Sélectionnez Office dans la liste **Programmes actuellement installés**.  
  
3.  Cliquez sur **Modifier**.  
  
4.  Sélectionnez **Ajouter ou supprimer des fonctionnalités**, puis cliquez sur **Continuer**.  
  
5.  Sélectionnez **Choisir la personnalisation avancée des applications**, puis cliquez sur **Suivant**.  
  
6.  Développez **Composants partagés d'Office** dans la liste **Choisissez les options de mise à jour pour les applications et les outils**.  
  
7.  Ouvrez le menu déroulant à côté de **Visual Basic pour Applications**, puis cliquez sur **Exécutez à partir du disque dur**.  
  
8.  Cliquez sur **Continuer**.  
  
9. Cliquez sur **Fermer**.  
  
### Pour réparer votre installation d'Office  
  
1.  Dans le Panneau de configuration, exécutez **Ajouter ou supprimer des programmes** ou **Programmes et fonctionnalités**.  
  
2.  Sélectionnez votre version d'Office dans la liste **Programmes actuellement installés**.  
  
3.  Cliquez sur **Modifier**.  
  
4.  Sélectionnez **Réinstaller ou réparer**, puis cliquez sur **Suivant**.  
  
5.  Sélectionnez **Détecter et réparer les erreurs de mon installation Office**, puis cliquez sur **Installer**.  
  
## Voir aussi  
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)  
  
  