---
title: Combinaison de VBA et personnalisations au niveau du Document | Documents Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
ms.assetid: 2c10feeb-38af-4802-bbf4-d637db81a884
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e8c9a3e0abdf478d6280795cd17b9b9a0bea0a13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="combining-vba-and-document-level-customizations"></a>Combinaison de VBA et de personnalisations au niveau du document
  Vous pouvez utiliser du code Visual Basic pour Applications (VBA) dans un document faisant partie d'une personnalisation au niveau du document pour Microsoft Office Word ou Microsoft Office Excel. Vous pouvez appeler du code VBA dans le document à partir de l'assembly de personnalisation ou configurer votre projet pour permettre au code VBA du document d'appeler du code dans l'assembly de personnalisation.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Comportement du code VBA dans une personnalisation au niveau du document  
 Quand vous ouvrez votre projet dans Visual Studio, le document s'ouvre en mode Design. Le code VBA ne s'exécute pas si le document est en mode Design, ce qui vous permet de travailler sur le document et de coder sans exécuter le code VBA.  
  
 Quand vous exécutez la solution, les gestionnaires d'événements dans le code VBA et l'assembly de personnalisation reprennent les événements déclenchés dans le document, et les deux ensembles de code sont exécutés. Il est impossible de savoir à l'avance quel code sera exécuté avant l'autre ; vous devez le déterminer en effectuant des tests dans chaque cas. Pour ne pas obtenir de résultats inattendus, prenez le temps de coordonner et de tester les deux jeux de code.  
  
## <a name="calling-vba-code-from-the-customization-assembly"></a>Appel du code VBA à partir de l'assembly de personnalisation  
 Vous pouvez appeler des macros dans les documents Word, ainsi que des macros et des fonctions dans les classeurs Excel. Pour ce faire, utilisez l'une des méthodes suivantes :  
  
-   Pour Word, appelez la méthode <xref:Microsoft.Office.Interop.Word._Application.Run%2A>de la classe <xref:Microsoft.Office.Interop.Word.Application> .  
  
-   Pour Excel, appelez la méthode <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> de la classe <xref:Microsoft.Office.Interop.Excel.Application> .  
  
 Pour chaque méthode, le premier paramètre identifie le nom de la macro ou de la fonction que vous souhaitez appeler, et les paramètres optionnels restants spécifient les paramètres à passer à la macro ou à la fonction. Le premier paramètre peut avoir des formats différents pour Word et Excel :  
  
-   Pour Word, le premier paramètre est une chaîne qui peut être toute combinaison de nom de modèle, de module et de macro. Si vous spécifiez le nom du document, votre code peut exécuter uniquement des macros dans les documents liés au contexte actuel (et non dans n'importe quelle macro de n'importe quel document).  
  
-   Pour Excel, le premier paramètre peut être une chaîne qui spécifie le nom de la macro, un <xref:Microsoft.Office.Interop.Excel.Range> qui indique où se trouve la fonction ou encore un ID de registre pour une fonction DLL (XLL) inscrite. Si vous passez une chaîne, la chaîne sera évaluée dans le contexte de la feuille active.  
  
 L'exemple de code suivant montre comment appeler une macro nommée `MyMacro` à partir d'un projet au niveau du document pour Excel. Cet exemple part du principe que `MyMacro` est défini dans `Sheet1`.  
  
```vb  
Globals.Sheet1.Application.Run("MyMacro")  
```  
  
```csharp  
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,   
    missing, missing, missing, missing, missing, missing);  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation de la variable globale `missing` à la place de paramètres facultatifs dans Visual C#, consultez [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="calling-code-in-document-level-customizations-from-vba"></a>Appel de code dans les personnalisations au niveau du document depuis VBA  
 Vous pouvez configurer un projet au niveau du document pour Word ou Excel de manière à ce que le code VBA dans le document puisse appeler le code dans l'assembly de personnalisation. Cela s'avère utile dans les scénarios suivant :  
  
-   Vous souhaitez étendre le code VBA existant dans un document à l'aide des fonctionnalités d'une personnalisation au niveau du document associée au même document.  
  
-   Vous souhaitez que les utilisateurs finaux puissent accéder aux services que vous développez dans une personnalisation au niveau du document en écrivant du code VBA dans le document.  
  
 Les Outils de développement Office dans Visual Studio offrent une fonctionnalité semblable pour les compléments VSTO. Si vous développez un complément VSTO, vous pouvez appeler du code dans votre complément VSTO à partir d’autres solutions Microsoft Office. Pour plus d'informations, consultez [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
> [!NOTE]  
>  Cette fonctionnalité ne peut pas être utilisée dans les projets de modèle Word. Elle ne peut l'être que dans des projets de document Word, de classeur Excel ou de modèle Excel.  
  
## <a name="requirements"></a>Configuration requise  
 Avant de pouvoir autoriser le code VBA à exécuter un appel dans l'assembly de personnalisation, votre projet doit remplir les conditions suivantes :  
  
-   Le document doit avoir l'une des extensions de nom de fichier suivantes :  
  
    -   Pour Word : .docm ou .doc  
  
    -   Pour Excel : .xlsm, .xltm, .xls ou .xlt  
  
-   Le document doit déjà contenir un projet VBA contenant du code VBA.  
  
-   Le code VBA dans le document doit être autorisé à s'exécuter sans inviter l'utilisateur à activer les macros. Vous pouvez approuver le code VBA à exécuter en ajoutant l'emplacement du projet Office à la liste des emplacements approuvés dans les paramètres du Centre de gestion de la confidentialité pour Word ou Excel.  
  
-   Le projet Office doit contenir au moins une classe publique contenant un ou plusieurs membres publics que vous exposez au code VBA.  
  
     Vous pouvez exposer des méthodes, des propriétés et des événements à VBA. La classe exposée peut être une classe d'élément hôte (telle que `ThisDocument` pour Word ou `ThisWorkbook` et `Sheet1` pour Excel) ou une autre classe définie dans votre projet. Pour plus d’informations sur les éléments hôtes, consultez [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="enabling-vba-code-to-call-into-the-customization-assembly"></a>Permettre au code VBA d'exécuter un appel dans l'assembly de personnalisation  
 Vous pouvez exposer les membres d'un assembly de personnalisation au code VBA dans le document de deux manières :  
  
-   Vous pouvez exposer les membres d'une classe d'élément hôte dans un projet [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] à VBA. Pour cela, affectez à la propriété **EnableVbaCallers** de l'élément hôte la valeur **True** dans la fenêtre **Propriétés** pendant que l'élément hôte (autrement dit, le document, la feuille de calcul ou le classeur) est ouvert dans le concepteur. Visual Studio exécute automatiquement tout le travail requis pour permettre au code VBA d'appeler des membres de la classe.  
  
-   Vous pouvez exposer à VBA des membres de n'importe quelle classe publique dans un projet Visual C# ou des membres d'une classe d'élément non hôte dans un projet [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] . Cette option vous offre davantage de liberté pour choisir les classes à exposer à VBA, mais elle nécessite également plus d'étapes manuelles.  
  
     Pour ce faire, vous devez effectuer les principales étapes suivantes :  
  
    1.  Exposez la classe à COM.  
  
    2.  Substituez la méthode **GetAutomationObject** d'une classe d'élément hôte de votre projet pour retourner une instance de la classe que vous exposez à VBA.  
  
    3.  Affectez à la propriété **ReferenceAssemblyFromVbaProject** de n'importe quelle classe d'élément hôte du projet la valeur **True**. Cela permet d'intégrer la bibliothèque de types de l'assembly de personnalisation à l'assembly et d'ajouter une référence à la bibliothèque de types au projet VBA du document.  
  
 Pour obtenir des instructions détaillées, consultez [Comment : exposer du Code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) et [Comment : exposer du Code à VBA dans un Visual C &#35; Projet](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 Les propriétés **EnableVbaCallers** et **ReferenceAssemblyFromVbaProject** sont uniquement disponibles dans la fenêtre **Propriétés** au moment du design ; elles ne peuvent pas être utilisées au moment de l'exécution. Pour afficher les propriétés, ouvrez le concepteur d'un élément hôte dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour plus d'informations sur les tâches spécifiques effectuées par Visual Studio quand vous définissez ces propriétés, consultez [Tâches effectuées par les propriétés d'élément hôte](#PropertyTasks).  
  
> [!NOTE]  
>  Si le classeur ou le document ne contient pas encore de code VBA ou que l'exécution du code VBA dans le document n'est pas approuvée, un message d'erreur s'affiche quand vous affectez à la propriété **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject** la valeur **True**. Cela est dû au fait que Visual Studio ne peut pas modifier le projet VBA dans le document dans cette situation.  
  
## <a name="using-members-in-vba-code-to-call-into-the-customization-assembly"></a>Utilisation de membres dans le code VBA pour exécuter un appel dans l'assembly de personnalisation  
 Après avoir configuré votre projet pour permettre au code VBA d'exécuter un appel dans l'assembly de personnalisation, Visual Studio ajoute les membres suivants au projet VBA dans le document :  
  
-   Pour tous les projets, Visual Studio ajoute une méthode globale nommée `GetManagedClass`.  
  
-   Pour les projets [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] dans lesquels vous exposez les membres d'une classe d'élément hôte à l'aide de la propriété **EnableVbaCallers** , Visual Studio ajoute également une propriété nommée `CallVSTOAssembly` au module `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`ou `Sheet3` dans le projet VBA.  
  
 Vous pouvez utiliser la propriété `CallVSTOAssembly` ou la méthode `GetManagedClass` pour accéder aux membres publics de la classe que vous avez exposée au code VBA dans le projet.  
  
> [!NOTE]  
>  Lors du développement et du déploiement de votre solution, vous pouvez ajouter le code VBA à plusieurs copies distinctes du document. Pour plus d'informations, consultez [Instructions concernant l'ajout de code VBA au document](#Guidelines).  
  
### <a name="using-the-callvstoassembly-property-in-a-visual-basic-project"></a>Utilisation de la propriété CallVSTOAssembly dans un projet Visual Basic  
 Utilisez la propriété `CallVSTOAssembly` pour accéder aux membres publics que vous avez ajoutés à la classe d'élément hôte. Par exemple, la macro VBA suivante appelle une méthode appelée `MyVSTOMethod` qui est définie dans la classe `Sheet1` d'un projet de classeur Excel.  
  
```  
Sub MyMacro()  
    Sheet1.CallVSTOAssembly.MyVSTOMethod()  
End Sub  
```  
  
 Il est plus pratique d'utiliser cette propriété pour exécuter un appel dans l'assembly de personnalisation que d'utiliser la méthode `GetManagedClass` directement. `CallVSTOAssembly` retourne un objet qui représente la classe d'élément hôte que vous avez exposée au code VBA. Les membres et paramètres de méthode de l'objet retourné apparaissent dans IntelliSense.  
  
 La propriété `CallVSTOAssembly` a une déclaration similaire au code suivant. Ce code part du principe que vous avez exposé la classe d'élément hôte `Sheet1` d'un projet de classeur Excel appelé `ExcelWorkbook1` à VBA.  
  
```  
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1  
    Set CallVSTOAssembly = GetManagedClass(Me)  
End Property  
```  
  
### <a name="using-the-getmanagedclass-method"></a>Utilisation de la méthode GetManagedClass  
 Pour utiliser la méthode `GetManagedClass` globale, passez l'objet VBA qui correspond à la classe d'élément hôte qui contient votre substitution de la méthode **GetAutomationObject** . Ensuite, utilisez l'objet retourné pour accéder à la classe que vous avez exposée à VBA.  
  
 Par exemple, la macro VBA suivante appelle une méthode nommée `MyVSTOMethod` définie dans la classe d'élément hôte `Sheet1` dans un projet de classeur Excel intitulé `ExcelWorkbook1`.  
  
```  
Sub CallVSTOMethod  
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1  
    Set VSTOSheet1 = GetManagedClass(Sheet1)  
    VSTOSheet1.MyVSTOMethod  
End Sub  
```  
  
 La méthode `GetManagedClass` contient la déclaration suivante :  
  
```  
GetManagedClass(pdispInteropObject Object) As Object  
```  
  
 Cette méthode retourne un objet qui représente la classe que vous avez exposée à VBA. Les membres et paramètres de méthode de l'objet retourné apparaissent dans IntelliSense.  
  
##  <a name="Guidelines"></a> Instructions concernant l'ajout de code VBA au document  
 Vous pouvez ajouter du code VBA qui exécute un appel dans la personnalisation au niveau du document à plusieurs copies distinctes du document.  
  
 Lors du développement et du test de votre solution, vous pouvez écrire du code VBA dans le document qui s'ouvre quand vous déboguez ou exécutez votre projet dans Visual Studio (autrement dit, le document situé dans le dossier de sortie de la génération). Le code VBA que vous ajoutez au document est toutefois substitué la prochaine fois que vous générez le projet, car Visual Studio remplace alors le document dans le dossier de sortie de la génération par une copie issue du dossier du projet principal.  
  
 Si vous souhaitez enregistrer le code VBA que vous ajoutez au document au moment du débogage ou de l'exécution de la solution, copiez le code VBA du document dans le dossier du projet. Pour plus d’informations sur le processus de génération, consultez [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
 Quand vous êtes prêt à déployer votre solution, vous pouvez ajouter le code VBA à trois emplacements principaux.  
  
### <a name="in-the-project-folder-on-the-development-computer"></a>Dans le dossier du projet sur l'ordinateur de développement  
 Cet emplacement est pratique si vous avez le contrôle complet du code VBA dans le document et le code de personnalisation. Comme le document est sur l'ordinateur de développement, vous pouvez facilement modifier le code VBA facilement si vous changez le code de personnalisation. Le code VBA que vous ajoutez à cette copie du document reste dans le document quand vous générez, déboguez et publiez votre solution.  
  
 Vous ne pouvez pas ajouter le code VBA au document pendant que celui-ci est ouvert dans le concepteur. Vous devez d'abord fermer le document dans le concepteur, puis ouvrir directement le document dans Word ou Excel.  
  
> [!CAUTION]  
>  Si vous ajoutez du code VBA qui s'exécute quand le document est ouvert, il peut arriver, dans de rares cas, que ce code endommage le document ou l'empêche de s'ouvrir dans le concepteur.  
  
### <a name="in-the-publish-or-installation-folder"></a>Dans le dossier de publication ou d'installation  
 Il peut parfois s'avérer approprié d'ajouter le code VBA au document dans le dossier de publication ou d'installation. Vous pouvez, par exemple, choisir cette option si le code VBA est écrit et testé par un développeur différent sur un ordinateur sur lequel Visual Studio n'est pas installé.  
  
 Si les utilisateurs installent directement la solution depuis le dossier de publication, vous devez ajouter le code VBA au document chaque fois que vous publiez la solution. Visual Studio remplace le document dans l'emplacement de publication quand vous publiez la solution.  
  
 Si les utilisateurs installent la solution à partir d'un dossier d'installation différent du dossier de publication, vous pouvez éviter d'ajouter le code VBA dans le document chaque fois que vous publiez la solution. Quand une mise à jour de publication est prête à être déplacée du dossier de publication vers celui d'installation, copiez tous les fichiers dans le dossier d'installation à l'exception du document.  
  
### <a name="on-the-end-user-computer"></a>Sur l'ordinateur de l'utilisateur final  
 Si les utilisateurs finaux sont des développeurs VBA qui appellent des services que vous fournissez dans la personnalisation au niveau du document, vous pouvez leur indiquer comment appeler votre code à l'aide de la propriété `CallVSTOAssembly` ou de la méthode `GetManagedClass` dans leurs propres copies du document. Quand vous publiez des mises à jour de la solution, le code VBA dans le document sur l'ordinateur de l'utilisateur final n'est pas remplacé, car le document n'est pas modifié par les mises à jour de publication.  
  
##  <a name="PropertyTasks"></a> Tâches effectuées par les propriétés d'élément hôte  
 Quand vous utilisez les propriétés **EnableVbaCallers** et **ReferenceAssemblyFromVbaProject** , Visual Studio exécute plusieurs ensembles de tâches.  
  
### <a name="enablevbacallers"></a>EnableVbaCallers  
 Quand vous affectez à la propriété **EnableVbaCallers** d'un élément hôte la valeur **True** dans un projet Visual Basic, Visual Studio effectue les tâches suivantes :  
  
1.  Il ajoute les attributs <xref:Microsoft.VisualBasic.ComClassAttribute> et <xref:System.Runtime.InteropServices.ComVisibleAttribute> à la classe d'élément hôte.  
  
2.  Il substitue la méthode **GetAutomationObject** de la classe d'élément hôte.  
  
3.  Il affecte à la propriété **ReferenceAssemblyFromVbaProject** de l'élément hôte la valeur **True**.  
  
 Quand vous affectez de nouveau à la propriété **EnableVbaCallers** la valeur **False**, Visual Studio effectue les tâches suivantes :  
  
1.  Il supprime les attributs <xref:Microsoft.VisualBasic.ComClassAttribute> et <xref:System.Runtime.InteropServices.ComVisibleAttribute> de la classe `ThisDocument` .  
  
2.  Il supprime la méthode **GetAutomationObject** de la classe d'élément hôte.  
  
    > [!NOTE]  
    >  Visual Studio n'affecte pas automatiquement à la propriété **ReferenceAssemblyFromVbaProject** de nouveau la valeur **False**. Vous pouvez affecter manuellement la valeur **False** à cette propriété à l'aide de la fenêtre **Propriétés** .  
  
### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject  
 Quand la propriété **ReferenceAssemblyFromVbaProject** d'un élément hôte dans un projet Visual Basic ou Visual C# a la valeur **True**, Visual Studio effectue les tâches suivantes :  
  
1.  Il génère une bibliothèque de types pour l'assembly de personnalisation et l'incorpore dans l'assembly.  
  
2.  Il ajoute une référence aux bibliothèques de types suivantes du projet VBA dans le document :  
  
    -   la bibliothèque de types de votre assembly de personnalisation ;  
  
    -   la bibliothèque de types Microsoft Visual Studio Tools pour Office Execution Engine 9.0 : cette bibliothèque de types est incluse dans [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 Quand vous affectez de nouveau à la propriété **ReferenceAssemblyFromVbaProject** la valeur **False**, Visual Studio effectue les tâches suivantes :  
  
1.  il supprime les références de la bibliothèque de types du projet VBA dans le document ;  
  
2.  il supprime la bibliothèque de types incorporée de l'assembly.  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 Le tableau suivant répertorie quelques erreurs courantes et des suggestions pour les résoudre.  
  
|Error|Suggestion|  
|-----------|----------------|  
|Après avoir défini la propriété **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject** , un message d'erreur déclare que le document ne contient pas de projet VBA ou que vous n'avez pas l'autorisation d'accéder au projet VBA du document.|Vérifiez que le document dans le projet contient au moins une macro VBA, que le projet VBA dispose d'un niveau de confiance suffisant pour s'exécuter et qu'il n'est pas protégé par un mot de passe.|  
|Après avoir défini la propriété **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject** , un message d'erreur indique que la déclaration <xref:System.Runtime.InteropServices.GuidAttribute> est manquante ou endommagée.|Vérifiez que la déclaration <xref:System.Runtime.InteropServices.GuidAttribute> est localisée dans le fichier AssemblyInfo.cs ou AssemblyInfo.vb de votre projet et que cet attribut possède un GUID valide.|  
|Après avoir défini la propriété **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject** , un message d'erreur indique que le numéro de version spécifié par <xref:System.Reflection.AssemblyVersionAttribute> n'est pas valide.|Vérifiez que la déclaration <xref:System.Reflection.AssemblyVersionAttribute> dans le fichier AssemblyInfo.cs ou AssemblyInfo.vb de votre projet est définie sur un numéro de version d'assembly valide. Pour plus d'informations sur les numéros de version d'assembly valides, consultez la classe <xref:System.Reflection.AssemblyVersionAttribute> .|  
|Après avoir renommé l'assembly de personnalisation, le code VBA qui exécute un appel dans l'assembly de personnalisation cesse de fonctionner.|Si vous modifiez le nom de l'assembly de personnalisation après l'avoir exposé au code VBA, le lien entre le projet VBA dans le document et votre assembly de personnalisation est rompu. Pour résoudre ce problème, remplacez la valeur de la propriété **ReferenceFromVbaAssembly** dans votre projet par **False** , puis à nouveau par **True**, et remplacez ensuite toutes les références à l'ancien nom de l'assembly dans le code VBA par le nouveau nom.|  
  
## <a name="see-also"></a>Voir aussi  
 [How to: Expose Code to VBA in a Visual Basic Project](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Comment : exposer du Code à VBA dans un Visual C &#35; Projet](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Procédure pas à pas : Appel de Code à partir de VBA dans un projet Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Procédure pas à pas : Code d’appel à partir de VBA dans un Visual C &#35; Projet](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Solutions VBA et Office dans Visual Studio par rapport](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)   
 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
  