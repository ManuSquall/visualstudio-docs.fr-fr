---
title: Appeler du code dans des compléments VSTO à partir d’autres solutions Office
description: Découvrez comment vous pouvez exposer un objet de votre complément VSTO à d’autres solutions, notamment d’autres solutions de Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: deb8fec9212c686bce670df6bab23ed56e51741f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903805"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Appeler du code dans des compléments VSTO à partir d’autres solutions Office
  Vous pouvez exposer un objet inclus dans votre complément VSTO à d’autres solutions, notamment d’autres solutions Microsoft Office. Cette possibilité s’avère utile si votre complément VSTO propose un service que vous voulez permettre à d’autres solutions d’utiliser. Par exemple, si vous avez un complément VSTO pour Microsoft Office Excel qui effectue des calculs sur des données financières à partir d’un service Web, d’autres solutions peuvent effectuer ces calculs en appelant le complément VSTO Excel au moment de l’exécution.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Deux étapes principales constituent ce processus :

- Dans le complément VSTO, exposez un objet à d’autres solutions.

- Dans une autre solution, accédez à l’objet exposé par votre complément VSTO, puis appelez des membres de l’objet.

## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Types de solutions pouvant appeler du code dans un complément
 Vous pouvez exposer un objet dans un complément VSTO aux types de solutions suivants :

- Code VBA (Visual Basic pour Applications) dans un document chargé dans le même processus d’application que votre complément VSTO.

- Personnalisations au niveau du document chargées dans le même processus d’application que votre complément VSTO.

- Autres compléments VSTO créés à l’aide de modèles de projet Office dans Visual Studio.

- Compléments VSTO COM (c’est-à-dire, des compléments VSTO qui implémentent l’interface <xref:Extensibility.IDTExtensibility2> directement).

- Toute solution qui s’exécute dans un autre processus que votre complément VSTO (ces types de solutions sont également appelés *clients hors processus*). Ces solutions incluent les applications qui automatisent une application Office, comme Windows Forms ou une application console, ainsi que les compléments VSTO chargés dans un processus différent.

## <a name="expose-objects-to-other-solutions"></a>Exposer des objets à d’autres solutions
 Pour exposer un objet inclus dans votre complément VSTO à d’autres solutions, procédez comme suit dans votre complément VSTO :

1. Définissez une classe que vous voulez exposer à d'autres solutions.

2. Substituez la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> dans la classe `ThisAddIn` . Retournez une instance de la classe que vous voulez exposer à d'autres solutions.

### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Définir la classe que vous voulez exposer à d’autres solutions
 Au minimum, la classe que vous voulez exposer doit être publique, son attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> doit avoir la valeur **true** et elle doit exposer l'interface [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) .

 La méthode recommandée pour exposer l'interface [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) consiste à procéder comme suit :

1. Définissez une interface qui déclare les membres que vous voulez exposer à d'autres solutions. Vous pouvez définir cette interface dans votre projet de complément VSTO. Toutefois, vous pouvez la définir dans un projet de bibliothèque de classes distinct si vous voulez exposer la classe à des solutions non-VBA. Ainsi, les solutions qui appellent votre complément VSTO peuvent référencer l’interface sans référencer votre projet de complément VSTO.

2. Appliquez l'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> à cette interface, puis affectez-y la valeur **true**.

3. Modifiez votre classe pour implémenter cette interface.

4. Appliquez l' <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribut à votre classe et affectez à cet attribut la valeur **None** de l' <xref:System.Runtime.InteropServices.ClassInterfaceType> énumération.

5. Si vous souhaitez exposer cette classe à des clients hors processus, vous devrez peut-être également effectuer les opérations suivantes :

   - Dérivez la classe de <xref:System.Runtime.InteropServices.StandardOleMarshalObject>. Pour plus d’informations, consultez [exposer des classes à des clients hors processus](#outofproc).

   - Définissez la propriété **Inscrire pour COM Interop** dans le projet où vous définissez l'interface. Cette propriété est nécessaire uniquement si vous souhaitez permettre aux clients d’utiliser la liaison précoce pour appeler le complément VSTO.

   L'exemple de code suivant présente une classe `AddInUtilities` avec une méthode `ImportData` que d'autres solutions peuvent appeler. Pour voir ce code dans le contexte d’une plus grande procédure pas à pas, consultez [procédure pas à pas : appeler du code dans un complément VSTO à partir de VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

   [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
   [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]

### <a name="expose-classes-to-vba"></a>Exposer des classes à VBA
 Quand vous effectuez les étapes indiquées ci-dessus, le code VBA peut uniquement appeler les méthodes que vous déclarez dans l'interface. Le code VBA ne peut pas appeler d'autres méthodes dans votre classe, notamment celles que votre classe obtient à partir des classes de base comme <xref:System.Object>.

 Vous pouvez également exposer l’interface [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) en affectant <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> à l’attribut la valeur AutoDispatch ou autodouble de l' <xref:System.Runtime.InteropServices.ClassInterfaceType> énumération. Si vous exposez l’interface, vous n’avez pas besoin de déclarer les méthodes dans une interface distincte. Toutefois, le code VBA peut appeler toutes les méthodes publiques et non statiques incluses dans votre classe, notamment celles obtenues à partir des classes de base comme <xref:System.Object>. En outre, les clients hors processus qui utilisent une liaison anticipée ne peuvent pas appeler votre classe.

### <a name="expose-classes-to-out-of-process-clients"></a><a name="outofproc"></a> Exposer des classes à des clients hors processus
 Si vous voulez exposer une classe dans votre complément VSTO à des clients hors processus, vous devez dériver la classe de <xref:System.Runtime.InteropServices.StandardOleMarshalObject> pour faire en sorte que les clients hors processus puissent appeler votre objet de complément VSTO exposé. Sinon, les tentatives d'obtention d'une instance de votre objet exposé dans un client hors processus risquent d'échouer de manière inattendue.

 Cet échec est dû au fait que tous les appels dans le modèle objet d’une application Office doivent être effectués sur le thread d’interface utilisateur principal, mais les appels d’un client hors processus à votre objet arrivent sur un thread RPC (Remote Procedure Call) arbitraire. Le mécanisme de marshaling COM dans le .NET Framework ne bascule pas de threads. En revanche, il essaie de marshaler l'appel à votre objet sur le thread RPC entrant au lieu du thread d'interface utilisateur principal. Si votre objet est une instance d'une classe qui dérive de <xref:System.Runtime.InteropServices.StandardOleMarshalObject>, les appels entrants à votre objet sont automatiquement marshalés au thread où l'objet exposé a été créé, à savoir le thread d'interface utilisateur principal de l'application hôte.

 Pour plus d’informations sur l’utilisation des threads dans les solutions Office, consultez [prise en charge des threads dans Office](../vsto/threading-support-in-office.md).

### <a name="override-the-requestcomaddinautomationservice-method"></a>Remplacer la méthode RequestComAddInAutomationService
 L'exemple de code suivant montre comment remplacer <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> dans la classe `ThisAddIn` de votre complément VSTO. L’exemple suppose que vous avez défini une classe nommée `AddInUtilities` que vous voulez exposer à d’autres solutions. Pour voir ce code dans le contexte d’une plus grande procédure pas à pas, consultez [procédure pas à pas : appeler du code dans un complément VSTO à partir de VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]

 Quand votre complément VSTO est chargé, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Le runtime assigne l’objet retourné à la propriété COMAddIn. Object d’un <xref:Microsoft.Office.Core.COMAddIn> objet qui représente votre complément VSTO. Cet objet <xref:Microsoft.Office.Core.COMAddIn> est disponible pour d'autres solutions Office et pour des solutions qui automatisent Office.

## <a name="access-objects-from-other-solutions"></a>Accéder aux objets à partir d’autres solutions
 Pour appeler l'objet exposé dans votre complément VSTO, procédez comme suit dans la solution cliente :

1. Obtenez l'objet <xref:Microsoft.Office.Core.COMAddIn> qui représente le complément VSTO exposé. Les clients peuvent accéder à tous les compléments VSTO disponibles en utilisant la propriété `Application.COMAddIns` dans le modèle objet de l'application Office hôte.

2. Accédez à la propriété COMAddIn. Object de l' <xref:Microsoft.Office.Core.COMAddIn> objet. Cette propriété retourne l'objet exposé à partir du complément VSTO.

3. Appelez les membres de l'objet exposé.

   La façon dont vous utilisez la valeur de retour de la propriété COMAddIn. Object est différente pour les clients VBA et les clients non-VBA. Pour les clients hors processus, du code supplémentaire est nécessaire pour éviter une éventuelle condition de concurrence.

### <a name="access-objects-from-vba-solutions"></a>Accéder aux objets à partir de solutions VBA
 L’exemple de code suivant montre comment utiliser VBA pour appeler une méthode exposée par un complément VSTO. Cette macro VBA appelle une méthode nommée `ImportData` qui est définie dans un complément VSTO nommé **ExcelImportData**. Pour voir ce code dans le contexte d’une plus grande procédure pas à pas, consultez [procédure pas à pas : appeler du code dans un complément VSTO à partir de VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

```vb
Sub CallVSTOMethod()
    Dim addIn As COMAddIn
    Dim automationObject As Object
    Set addIn = Application.COMAddIns("ExcelImportData")
    Set automationObject = addIn.Object
    automationObject.ImportData
End Sub
```

### <a name="access-objects-from-non-vba-solutions"></a>Accéder aux objets à partir de solutions non-VBA
 Dans une solution non-VBA, vous devez effectuer un cast de la valeur de la propriété COMAddIn. Object vers l’interface qu’elle implémente, puis vous pouvez appeler les méthodes exposées sur l’objet interface. L'exemple de code suivant montre comment appeler la méthode `ImportData` d'un autre complément VSTO créé à l'aide des Outils de développement Office dans Visual Studio.

```vb
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _
    addIn.Object, ExcelImportData.IAddInUtilities)
utilities.ImportData()
```

```csharp
object addInName = "ExcelImportData";
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;
utilities.ImportData();
```

 Dans cet exemple, si vous essayez d’effectuer un cast de la valeur de la propriété COMAddIn. Object vers la `AddInUtilities` classe plutôt que l' `IAddInUtilities` interface, le code lève une <xref:System.InvalidCastException> .

## <a name="see-also"></a>Voir aussi
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Procédure pas à pas : appel de code dans un complément VSTO à partir de VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Développer des solutions Office](../vsto/developing-office-solutions.md)
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Personnaliser les fonctionnalités de l’interface utilisateur à l’aide des interfaces d’extensibilité](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
