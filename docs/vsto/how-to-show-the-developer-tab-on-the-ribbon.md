---
title: "Comment&#160;: afficher l&#39;onglet D&#233;veloppeur sur le ruban"
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
  - "Développeur (onglet) (développement Office dans Visual Studio)"
  - "ruban (développement Office dans Visual Studio), onglets"
ms.assetid: ce7cb641-44f2-4a40-867e-a7d88f8e98a9
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Comment&#160;: afficher l&#39;onglet D&#233;veloppeur sur le ruban
  Pour accéder à l'onglet **Développeur** sur le ruban d'une application Office, vous devez configurer cette dernière pour afficher l'onglet, car il n'apparaît pas par défaut.  Par exemple, vous devez afficher cet onglet pour ajouter un <xref:Microsoft.Office.Tools.Word.GroupContentControl> à une personnalisation au niveau du document pour Word.  
  
> [!NOTE]  
>  Ces informations d'aide s'appliquent uniquement aux applications Office 2010 ou version ultérieure.  Pour afficher cet onglet dans Microsoft Office System 2007, consultez la version suivante de cette rubrique : [Comment : afficher l'onglet Développeur sur le ruban](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Access n'a pas d'onglet **Développeur**.  
  
### Pour afficher l'onglet Développeur  
  
1.  Démarrez l'une des applications Office prises en charge dans cette rubrique.  Reportez\-vous à la remarque **S'applique à :**, précédemment dans cette rubrique.  
  
2.  Sous l'onglet **Fichier**, choisissez le bouton **Options**.  
  
     L'illustration suivante montre l'onglet **Fichier** et le bouton **Options** dans Office 2010.  
  
     ![Choix de fichier, Options dans Outlook 2010](../vsto/media/vsto-office-file-tab.png "Choix de fichier, Options dans Outlook 2010")  
  
     L'illustration suivante montre l'onglet **Fichier** dans Office 2013.  
  
     ![Onglet Fichier dans Outlook 2013](../vsto/media/vsto-office2013-filetab.png "Onglet Fichier dans Outlook 2013")  
  
     L'illustration suivante montre le bouton **Options** dans Office 2013.  
  
     ![Bouton Options dans Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "Bouton Options dans Outlook 2013 Preview")  
  
3.  Dans la boîte de dialogue **Options** *Nom\_application*, choisissez le bouton **Personnaliser le Ruban**.  
  
     L'illustration suivante montre la boîte de dialogue **Options** et le bouton **Personnaliser le Ruban** dans Excel 2010.  L'emplacement de ce bouton est similaire dans toutes les autres applications répertoriées dans la section « S'applique à » au début de cette rubrique.  
  
     ![Bouton Personnaliser le Ruban](../vsto/media/vsto-office2010-customizeribbonbutton.png "Bouton Personnaliser le Ruban")  
  
4.  Dans la liste des onglets principaux, cochez la case **Développeur**.  
  
     L'illustration suivante montre la case à cocher **Développeur** dans Word 2010 et [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)].  L'emplacement de cette case à cocher est similaire dans toutes les autres applications répertoriées dans la section « S'applique à » au début de cette rubrique.  
  
     ![Case à cocher « Développeur » dans la boîte de dialogue Options Word](../vsto/media/vsto-office2010-developercheckbox.png "Case à cocher « Développeur » dans la boîte de dialogue Options Word")  
  
5.  Choisissez le bouton **OK** pour fermer la boîte de dialogue **Options**.  
  
## Voir aussi  
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)  
  
  