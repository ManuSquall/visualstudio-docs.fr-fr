---
title: "Comment&#160;: exposer du code &#224; VBA dans un projet Visual&#160;C#"
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
  - "VBA (développement Office dans Visual Studio), exposer du code dans les personnalisations au niveau du document"
  - "Visual C# (développement Office dans Visual Studio), exposer du code à VBA"
ms.assetid: 56d5894b-4823-42f4-8c7e-d8739b859c52
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Comment&#160;: exposer du code &#224; VBA dans un projet Visual&#160;C# #
  Vous pouvez exposer du code dans un projet Visual C\# à du code Visual Basic pour applications \(VBA\) si vous souhaitez que les deux types de code interagissent.  
  
 Le processus Visual C\# est différent du processus Visual Basic.  Pour plus d’informations, consultez [Comment : exposer du code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Exposer le code dans un projet Visual C\#  
 Pour permettre à du code VBA d'appeler du code dans un projet Visual C\#, modifiez le code de sorte qu'il soit visible à COM, puis affectez à la propriété **ReferenceAssemblyFromVbaProject** la valeur **True** dans le concepteur.  
  
 Pour une procédure pas à pas montrant comment appeler une méthode dans un projet Visual C\# de VBA, consultez [Procédure pas à pas : appel de code à partir de VBA dans un projet Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
#### Pour exposer le code dans un projet Visual C\# à VBA  
  
1.  Ouvrez ou créez un projet au niveau du document basé sur un document Word, un classeur Excel ou un modèle Excel qui prend en charge des macros et qui contient déjà du code VBA.  
  
     Pour plus d'informations sur les formats de fichier de document qui prennent en charge des macros, consultez [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Cette fonctionnalité ne peut pas être utilisée dans des projets de modèle Word.  
  
2.  Assurez\-vous que le code VBA du document peut s'exécuter sans inviter l'utilisateur à activer des macros.  Vous pouvez approuver le code VBA à exécuter en ajoutant l'emplacement du projet Office à la liste des emplacements approuvés dans les paramètres du Centre de gestion de la confidentialité pour Word ou Excel.  
  
3.  Ajoutez le membre que vous souhaitez exposer à VBA à une classe publique dans votre projet et déclarez le nouveau membre comme **public**.  
  
4.  Appliquez les attributs <xref:System.Runtime.InteropServices.ComVisibleAttribute> et <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> à la classe que vous exposez à VBA.  Ces attributs permettent à COM de voir la classe, mais sans générer d'interface de classe.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Substituez la méthode **GetAutomationObject** d'une classe d'élément hôte de votre projet pour retourner une instance de la classe que vous exposez à VBA :  
  
    -   Si vous exposez une classe d'élément hôte à VBA, substituez la méthode **GetAutomationObject** qui appartient à cette classe et retournez l'instance actuelle de la classe.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Si vous exposez à VBA une classe qui n'est pas un élément hôte, substituez la méthode **GetAutomationObject** de tout élément hôte dans votre projet et retournez une instance de la classe d'élément non hôte.  Par exemple, le code suivant suppose que vous exposez à VBA une classe appelée `DocumentUtilities`.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Pour plus d'informations sur les éléments hôtes, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Extrayez une interface de la classe que vous exposez à VBA.  Dans la boîte de dialogue **Extraire l'interface**, sélectionnez les membres publics que vous souhaitez inclure dans la déclaration d'interface.  Pour plus d’informations, consultez [Extract Interface Refactoring &#40;C&#35;&#41;](../csharp-ide/extract-interface-refactoring-csharp.md).  
  
7.  Ajoutez le mot clé **public** à la déclaration d'interface.  
  
8.  Rendez l'interface visible à COM en ajoutant l'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> suivant à l'interface.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Ouvrez le document \(pour Word\) ou la feuille de calcul \(pour Excel\) dans le concepteur dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. Dans la fenêtre **Propriétés**, sélectionnez la propriété **ReferenceAssemblyFromVbaProject** et remplacez sa valeur par **True**.  
  
    > [!NOTE]  
    >  Si le classeur ou le document ne contient pas encore de code VBA ou si l'exécution du code VBA du document n'est pas approuvée, un message d'erreur s'affiche lorsque vous affectez la valeur **True** à la propriété **ReferenceAssemblyFromVbaProject**.  Cela est dû au fait que Visual Studio ne peut pas modifier le projet VBA dans le document dans ce type de situation.  
  
11. Cliquez sur **OK** en réponse au message qui s'affiche.  Ce message vous rappelle que si vous ajoutez du code VBA au classeur ou au document lors de l'exécution du projet à partir de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], le code VBA sera perdu la prochaine fois que vous générez le projet.  Cela est dû au fait que le document du dossier de sortie de la génération est remplacé lors de chaque génération du projet.  
  
     À ce stade, Visual Studio configure le projet afin que le projet VBA puisse appeler l'assembly.  Visual Studio ajoute également la méthode appelée `GetManagedClass` au projet VBA.  Vous pouvez appeler cette méthode à partir de n'importe quel endroit dans le projet VBA pour accéder à la classe que vous avez exposée à VBA.  
  
12. Générez le projet.  
  
## Voir aussi  
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)   
 [Procédure pas à pas : appel de code à partir de VBA dans un projet Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Comment : exposer du code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  