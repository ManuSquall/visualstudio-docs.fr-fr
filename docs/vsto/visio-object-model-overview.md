---
title: Présentation du modèle objet de Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 040144b1e18e216ef8ceadbd218cd42ccf7c40f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848465"
---
# <a name="visio-object-model-overview"></a>Présentation du modèle objet de Visio
  Pour développer les solutions Office pour Microsoft Office Visio, vous pouvez interagir avec le modèle objet Visio. Ce modèle objet se compose de classes et d'interfaces qui sont fournies dans l'assembly PIA de Visio et définies dans l'espace de noms `Microsoft.Office.Interop.Visio`.  
  
 Cette rubrique propose une brève vue d'ensemble du modèle objet Excel. Pour plus d'informations sur l'utilisation du modèle objet Visio pour exécuter des tâches dans les projets Office, consultez les rubriques suivantes :  
  
-   [Travailler avec des documents Visio](../vsto/working-with-visio-documents.md)  
  
-   [Utilisez des formes Visio](../vsto/working-with-visio-shapes.md)  
  
## <a name="understand-the-visio-object-model"></a>Comprendre le modèle objet Visio  
 Visio fournit de nombreux objets avec lesquels vous pouvez interagir. Ces objets sont organisés selon une hiérarchie qui suit étroitement l'interface utilisateur. En haut de la hiérarchie se trouve l'objet [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) . Cet objet représente l'instance en cours de Visio. Le `Microsoft.Office.Interop.Visio.Application` objet contient la `Microsoft.Office.Interop.Visio.Document` et `Microsoft.Office.Interop.Visio.Page` objets ainsi que la `Microsoft.Office.Interop.Visio.Documents` et `Microsoft.Office.Interop.Visio.Pages` collections. Chacun de ces objets et collections possède de nombreuses méthodes et propriétés auxquelles vous pouvez accéder pour le manipuler et interagir avec lui.  
  
 Pour plus d’informations, consultez la documentation de référence VBA [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document), et [ Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) objets, ainsi que la [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) et [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) Collections.  
  
 Les sections suivantes décrivent brièvement les objets de niveau supérieur et la façon dont ils interagissent les uns avec les autres. Ces objets incluent les éléments suivants :  
  
-   Objet Application  
  
-   Objet Document  
  
-   Page (objet)  
  
### <a name="application-object"></a>Objet Application  
 L’objet Microsoft.Office.Interop.Visio.Application représente l’application Visio et est le parent de tous les autres objets. Ses membres s'appliquent généralement à Visio dans son ensemble. Vous pouvez utiliser les propriétés et méthodes de la Microsoft.Office.Interop.Visio.Application et `Microsoft.Office.Interop.Visio.ApplicationSettings` objets pour contrôler l’environnement Visio.  
  
 Dans les projets de complément VSTO, vous pouvez accéder à l’objet Microsoft.Office.Interop.Visio.Application à l’aide de la `Application` champ la `ThisAddIn` classe. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
### <a name="document-object"></a>Objet Document  
 L’objet Microsoft.Office.Interop.Visio.Document est essentiel à la programmation de Visio. Il représente un fichier de dessin, de gabarit ou de modèle. Lorsque vous ouvrez un document Visio ou créez un nouveau document, vous créez un nouvel objet Microsoft.Office.Interop.Visio.Document, qui est ajouté à la collection de l’objet Microsoft.Office.Interop.Visio.Application Microsoft.Office.Interop.Visio.Documents .  
  
 Le document qui a le focus est appelé le document actif. Il est représenté par le `Microsoft.Office.Interop.Visio.Application.ActiveDocument` propriété de l’objet Microsoft.Office.Interop.Visio.Application.  
  
### <a name="page-object"></a>Page (objet)  
 L’objet Microsoft.Office.Interop.Visio.Page représente la zone de dessin d’une page de premier plan ou d’arrière-plan. Vous pouvez utiliser la propriété `Microsoft.Office.Interop.Visio.Page.Background` pour déterminer si une page est une page de premier plan ou d'arrière-plan.  
  
 Pour créer des formes, vous pouvez utiliser les méthodes qui incluent les méthodes `Microsoft.Office.Interop.Visio.Page.DrawSpline` et `Microsoft.Office.Interop.Visio.Page.DrawOval`. En outre, vous pouvez récupérer des formes de base de gabarits et placer ces formes sur une page à l'aide des méthodes `Microsoft.Office.Interop.Visio.Page.Drop` ou `Microsoft.Office.Interop.Visio.Page.DropMany`.  
  
## <a name="use-the-visio-object-model-documentation"></a>Utilisez la documentation du modèle objet Visio  
 Pour obtenir des informations complètes sur le modèle objet Visio, vous pouvez vous reporter à la référence du modèle objet Visio VBA. La documentation du modèle objet VBA présente le modèle objet Visio tel qu'il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [référence du modèle objet Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA Visio. Par exemple, le `Document` objet dans la référence du modèle objet VBA correspond au type Microsoft.Office.Interop.Visio.Document dans l’assembly PIA Visio. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet de complément VSTO Visio créé à l'aide de Visual Studio.  
  
> [!NOTE]  
>  À ce stade, il n'existe aucune documentation de référence pour l'assembly PIA Visio.  
  
 Pour plus d’exemples de code associés et des outils supplémentaires pour la création de solutions Visio, consultez [kit de développement logiciel Visio 2010](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### <a name="additional-types-in-primary-interop-assemblies"></a>Types supplémentaires dans les assemblys PIA  
 Vous pouvez trouver des types dans les assemblys PIA qui ne sont pas visibles par VBA en raison des différences d'implémentation. VBA fournit une vue du modèle objet Visio qui inclut uniquement les objets et les membres que vous pouvez utiliser directement. Les assemblys PIA exposent le même modèle objet, mais incluent également les autres interfaces, classes et membres qui convertissent les objets du modèle objet COM en code managé. Ces éléments supplémentaires ne sont pas destinés à être utilisés directement dans votre code.  
  
 Pour plus d’informations, consultez [vue d’ensemble des classes et interfaces dans les assemblys PIA Office](http://go.microsoft.com/fwlink/?LinkId=189592) et [assemblys PIA Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Travailler avec des documents Visio](../vsto/working-with-visio-documents.md)   
 [Utilisez des formes Visio](../vsto/working-with-visio-shapes.md)  
