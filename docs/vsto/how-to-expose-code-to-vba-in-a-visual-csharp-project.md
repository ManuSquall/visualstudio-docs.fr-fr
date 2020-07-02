---
title: 'Comment : exposer du code à VBA dans un projet C#'
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 21d7672d3c08012e75d73ee8bf4d9816b850eb2c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544831"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Comment : exposer du code à VBA dans un projet Visual C#
  Vous pouvez exposer du code dans un projet Visual C# à du code Visual Basic pour Applications (VBA) si vous souhaitez que les deux types de code interagissent les uns avec les autres.

 Le processus Visual C# est différent du processus de Visual Basic. Pour plus d’informations, consultez [Comment : exposer du code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Exposer du code dans un projet Visual C#
 Pour permettre au code VBA d’appeler du code dans un projet Visual C#, modifiez le code afin qu’il soit visible par COM, puis affectez la **valeur true** à la propriété **ReferenceAssemblyFromVbaProject** dans le concepteur.

 Pour obtenir une procédure pas à pas qui montre comment appeler une méthode dans un projet Visual C# à partir de VBA, consultez [procédure pas à pas : appeler du code à partir de VBA dans un projet Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Pour exposer du code dans un projet Visual C# à VBA

1. Ouvrez ou créez un projet au niveau du document basé sur un document Word, un classeur Excel ou un modèle Excel qui prend en charge les macros, et qui contient déjà du code VBA.

    Pour plus d’informations sur les formats de fichier de document qui prennent en charge les macros, consultez [combiner des personnalisations VBA et au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).

   > [!NOTE]
   > Cette fonctionnalité ne peut pas être utilisée dans les projets de modèle Word.

2. Veillez à ce que le code VBA dans le document soit autorisé à s’exécuter sans inviter l’utilisateur à activer les macros. Vous pouvez approuver le code VBA à exécuter en ajoutant l'emplacement du projet Office à la liste des emplacements approuvés dans les paramètres du Centre de gestion de la confidentialité pour Word ou Excel.

3. Ajoutez le membre que vous souhaitez exposer à VBA à une classe publique dans votre projet, puis déclarez le nouveau membre comme **public**.

4. Appliquez les <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributs et suivants <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> à la classe que vous exposez à VBA. Ces attributs rendent la classe visible pour COM, mais ne génèrent pas d'interface de classe.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. Substituez la méthode **GetAutomationObject** d’une classe d’élément hôte de votre projet pour retourner une instance de la classe que vous exposez à VBA :

   - Si vous exposez une classe d’élément hôte à VBA, substituez la méthode **GetAutomationObject** qui appartient à cette classe et retournez l’instance actuelle de la classe.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - Si vous exposez une classe qui n’est pas un élément hôte à VBA, substituez la méthode **GetAutomationObject** de tout élément hôte de votre projet et retournez une instance de la classe d’élément non-hôte. Par exemple, le code suivant suppose que vous exposez une classe nommée `DocumentUtilities` à VBA.

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Pour plus d’informations sur les éléments hôtes, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).

6. Extrayez une interface de la classe que vous exposez à VBA. Dans la boîte de dialogue **extraire l’interface** , sélectionnez les membres publics que vous souhaitez inclure dans la déclaration d’interface. Pour plus d’informations, consultez [extraire l’interface, refactorisation](../ide/reference/extract-interface.md).

7. Ajoutez le mot clé **public** à la déclaration de l’interface.

8. Rendez l’interface visible par COM en ajoutant l' <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribut suivant à l’interface.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. Ouvrez le document (pour Word) ou la feuille de calcul (pour Excel) dans le concepteur de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

10. Dans la fenêtre **Propriétés** , sélectionnez la propriété **ReferenceAssemblyFromVbaProject** et remplacez sa valeur par **True**.

    > [!NOTE]
    > Si le classeur ou le document ne contient pas encore de code VBA ou si l’exécution du code VBA dans le document n’est pas approuvée, vous recevrez un message d’erreur lorsque vous affectez à la propriété **ReferenceAssemblyFromVbaProject** la **valeur true**. Cela est dû au fait que Visual Studio ne peut pas modifier le projet VBA dans le document dans cette situation.

11. Cliquez sur **OK** dans le message qui s'affiche. Ce message vous rappelle que si vous ajoutez du code VBA au classeur ou au document lors de l’exécution du projet à partir de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , le code VBA sera perdu la prochaine fois que vous générerez le projet. Cela est dû au fait que le document dans le dossier de sortie de la génération est remplacé chaque fois que vous générez le projet.

     À ce stade, Visual Studio configure le projet afin que le projet VBA puisse appeler l’assembly. Visual Studio ajoute également une méthode nommée `GetManagedClass` au projet VBA. Vous pouvez appeler cette méthode à partir de n’importe où dans le projet VBA pour accéder à la classe que vous avez exposée à VBA.

12. Créez le projet.

## <a name="see-also"></a>Voir aussi
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Combiner VBA et les personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)
- [Procédure pas à pas : appel de code à partir de VBA dans un projet Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Comment : exposer du code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
