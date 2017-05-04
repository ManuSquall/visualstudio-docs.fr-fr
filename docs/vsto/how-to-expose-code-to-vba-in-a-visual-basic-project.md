---
title: "Comment&#160;: exposer du code &#224; VBA dans un projet Visual Basic | Microsoft Docs"
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
  - "personnalisations au niveau du document (développement Office dans Visual Studio), exposer du code"
  - "exposer du code à VBA"
  - "éléments hôtes (développement Office dans Visual Studio), exposer du code à VBA"
  - "VBA (développement Office dans Visual Studio), exposer du code dans les personnalisations au niveau du document"
  - "Visual Basic (développement Office dans Visual Studio), exposer du code à VBA"
ms.assetid: dc74f3ea-3f78-47f8-8a82-a67896144dd9
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Comment&#160;: exposer du code &#224; VBA dans un projet Visual Basic
  Vous pouvez exposer du code dans un projet [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] à du code Visual Basic pour applications \(VBA\) si vous souhaitez que les deux types de code interagissent.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Le processus Visual Basic est différent du processus Visual C\#.  Pour plus d’informations, consultez [Comment : exposer du code à VBA dans un projet Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 Le processus est différent pour le code dans une classe d'élément hôte et pour le code dans d'autres classes :  
  
-   [Exposition d'un code dans une classe d'élément hôte](#HostItemCode)  
  
-   [Exposition d'un code qui n'est pas dans une classe d'élément hôte](#NonHostItem)  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour une démonstration vidéo connexe, consultez [How Do I: Call VSTO Code from VBA?](http://go.microsoft.com/fwlink/?LinkId=136757) \(page éventuellement en anglais\).  
  
##  <a name="HostItemCode"></a> Exposition d'un code dans une classe d'élément hôte  
 Pour permettre au code VBA d'appeler le code Visual Basic dans une classe d'élément hôte, affectez la valeur **True** à la propriété **EnableVbaCallers** de l'élément hôte.  
  
 Pour une procédure pas à pas qui montre comment exposer une méthode d'une classe d'élément hôte et comment l'appeler à partir de code VBA, consultez [Procédure pas à pas : appel de code à partir de VBA dans un projet Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  Pour plus d'informations sur les éléments hôtes, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
#### Pour exposer un code dans un élément hôte à VBA  
  
1.  Ouvrez ou créez un projet [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] au niveau du document basé sur un document Word, un classeur Excel ou un modèle Excel qui prend en charge des macros et qui contient déjà du code VBA.  
  
     Pour plus d'informations sur les formats de fichier de document qui prennent en charge des macros, consultez [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Cette fonctionnalité ne peut pas être utilisée dans des projets de modèle Word.  
  
2.  Assurez\-vous que le code VBA du document peut s'exécuter sans inviter l'utilisateur à activer des macros.  Vous pouvez approuver le code VBA à exécuter en ajoutant l'emplacement du projet Office à la liste des emplacements approuvés dans les paramètres du Centre de gestion de la confidentialité pour Word ou Excel.  
  
3.  Ajoutez la propriété, la méthode ou l'événement que vous souhaitez exposer à VBA à l'une des classes d'élément hôte dans votre projet et déclarez le nouveau membre comme **Public**.  Le nom de la classe dépend de l'application :  
  
    -   Dans un projet Word, la classe d'élément hôte est intitulée `ThisDocument` par défaut.  
  
    -   Dans un projet Excel, les classes d'élément hôte s'appellent par défaut `ThisWorkbook`, `Sheet1`, `Sheet2` et `Sheet3`.  
  
4.  Affectez la valeur **True** à la propriété **EnableVbaCallers** pour l'élément hôte.  Cette propriété est disponible dans la fenêtre **Propriétés** lorsque l'élément hôte est ouvert dans le concepteur.  
  
     Une fois cette propriété définie, Visual Studio affecte automatiquement à la propriété **ReferenceAssemblyFromVbaProject** la valeur **True**.  
  
    > [!NOTE]  
    >  Si le classeur ou le document ne contient pas encore de code VBA, ou si l'exécution du code VBA du document n'est pas approuvée, un message d'erreur s'affiche lorsque vous affectez la valeur **True** à la propriété **EnableVbaCallers**.  Cela est dû au fait que Visual Studio ne peut pas modifier le projet VBA dans le document dans ce type de situation.  
  
5.  Cliquez sur **OK** en réponse au message qui s'affiche.  Ce message vous rappelle que si vous ajoutez du code VBA au classeur ou au document lors de l'exécution du projet à partir de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], le code VBA sera perdu la prochaine fois que vous génèrerez le projet.  La raison en est que le document du dossier de sortie de la génération est remplacé lors de chaque génération du projet.  
  
     À ce stade, Visual Studio configure le projet afin que le projet VBA puisse appeler l'assembly.  Visual Studio ajoute également une propriété nommée `CallVSTOAssembly` au module `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2` ou `Sheet3` dans le projet VBA.  Vous pouvez utiliser cette propriété pour accéder aux membres publics de la classe que vous avez exposée à VBA.  
  
6.  Générez le projet.  
  
##  <a name="NonHostItem"></a> Exposition d'un code qui n'est pas dans une classe d'élément hôte  
 Pour permettre au code VBA d'appeler un code Visual Basic qui n'est pas dans une classe d'élément hôte, modifiez le code de manière à ce qu'il soit visible pour VBA.  
  
#### Pour exposer un code qui n'est pas dans une classe d'élément hôte à VBA  
  
1.  Ouvrez ou créez un projet [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] au niveau du document basé sur un document Word, un classeur Excel ou un modèle Excel qui prend en charge des macros et qui contient déjà du code VBA.  
  
     Pour plus d'informations sur les formats de fichier de document qui prennent en charge des macros, consultez [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Cette fonctionnalité ne peut pas être utilisée dans des projets de modèle Word.  
  
2.  Assurez\-vous que le code VBA du document peut s'exécuter sans inviter l'utilisateur à activer des macros.  Vous pouvez approuver le code VBA à exécuter en ajoutant l'emplacement du projet Office à la liste des emplacements approuvés dans les paramètres du Centre de gestion de la confidentialité pour Word ou Excel.  
  
3.  Ajoutez le membre que vous souhaitez exposer à VBA à une classe publique dans votre projet et déclarez le nouveau membre comme **public**.  
  
4.  Appliquez les attributs <xref:System.Runtime.InteropServices.ComVisibleAttribute> et <xref:Microsoft.VisualBasic.ComClassAttribute> à la classe que vous exposez à VBA.  Ces attributs rendent la classe visible pour VBA.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Substituez la méthode **GetAutomationObject** d'une classe d'élément hôte de votre projet pour retourner une instance de la classe que vous exposez à VBA.  L'exemple de code suivant suppose que vous exposez à VBA une classe appelée `DocumentUtilities`.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Ouvrez le concepteur de document \(pour Word\) ou de feuille de calcul \(pour Excel\) dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  Dans la fenêtre **Propriétés**, sélectionnez la propriété **ReferenceAssemblyFromVbaProject** et remplacez sa valeur par **True**.  
  
    > [!NOTE]  
    >  Si le classeur ou le document ne contient pas encore de code VBA ou si l'exécution du code VBA du document n'est pas approuvée, un message d'erreur s'affiche lorsque vous affectez la valeur **True** à la propriété **ReferenceAssemblyFromVbaProject**.  Cela est dû au fait que Visual Studio ne peut pas modifier le projet VBA dans le document dans ce type de situation.  
  
8.  Cliquez sur **OK** en réponse au message qui s'affiche.  Ce message vous rappelle que si vous ajoutez du code VBA au classeur ou au document lors de l'exécution du projet à partir de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], le code VBA sera perdu la prochaine fois que vous génèrerez le projet.  La raison en est que le document du dossier de sortie de la génération est remplacé lors de chaque génération du projet.  
  
     À ce stade, Visual Studio configure le projet afin que le projet VBA puisse appeler l'assembly.  Visual Studio ajoute également la méthode appelée `GetManagedClass` au projet VBA.  Vous pouvez appeler cette méthode à partir de n'importe quel endroit dans le projet VBA pour accéder à la classe que vous avez exposée à VBA.  
  
9. Générez le projet.  
  
## Voir aussi  
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)   
 [Procédure pas à pas : appel de code à partir de VBA dans un projet Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Comment : exposer du code à VBA dans un projet Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  