---
title: Vue d’ensemble du modèle objet Visio
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 88695511d22e38262dc969d66e469441c9c3ac47
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985480"
---
# <a name="visio-object-model-overview"></a>Vue d’ensemble du modèle objet Visio
  Pour développer les solutions Office pour Microsoft Office Visio, vous pouvez interagir avec le modèle objet Visio. Ce modèle objet se compose de classes et d'interfaces qui sont fournies dans l'assembly PIA de Visio et définies dans l'espace de noms `Microsoft.Office.Interop.Visio`.

 Cette rubrique propose une brève vue d'ensemble du modèle objet Excel. Pour plus d'informations sur l'utilisation du modèle objet Visio pour exécuter des tâches dans les projets Office, consultez les rubriques suivantes :

- [Utiliser des documents Visio](../vsto/working-with-visio-documents.md)

- [Utiliser des formes Visio](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Comprendre le modèle objet Visio
 Visio fournit de nombreux objets avec lesquels vous pouvez interagir. Ces objets sont organisés selon une hiérarchie qui suit étroitement l'interface utilisateur. En haut de la hiérarchie se trouve l'objet [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) . Cet objet représente l'instance en cours de Visio. L’objet `Microsoft.Office.Interop.Visio.Application` contient les objets `Microsoft.Office.Interop.Visio.Document` et `Microsoft.Office.Interop.Visio.Page` ainsi que les collections `Microsoft.Office.Interop.Visio.Documents` et `Microsoft.Office.Interop.Visio.Pages`. Chacun de ces objets et collections possède de nombreuses méthodes et propriétés auxquelles vous pouvez accéder pour le manipuler et interagir avec lui.

 Pour plus d’informations, consultez la documentation de référence VBA pour les objets [Microsoft. Office. Interop. Visio. application](/office/vba/api/Visio.Application), [Microsoft. Office. Interop. Visio. document](/office/vba/api/Visio.Document)et [Microsoft. Office. Interop. Visio. page](/office/vba/api/Visio.Page) , ainsi que le [ Collections Microsoft. Office. Interop. Visio. documents](/office/vba/api/Visio.Documents) et [Microsoft. Office. Interop. Visio. pages](/office/vba/api/Visio.Pages) .

 Les sections suivantes décrivent brièvement les objets de niveau supérieur et la façon dont ils interagissent les uns avec les autres. Ces objets incluent les éléments suivants :

- Objet Application

- Objet Document

- Page (objet)

### <a name="application-object"></a>Objet Application
 L’objet Microsoft. Office. Interop. Visio. application représente l’application Visio et est le parent de tous les autres objets. Ses membres s'appliquent généralement à Visio dans son ensemble. Vous pouvez utiliser les propriétés et les méthodes des objets Microsoft. Office. Interop. Visio. application et `Microsoft.Office.Interop.Visio.ApplicationSettings` pour contrôler l’environnement Visio.

 Dans les projets de complément VSTO, vous pouvez accéder à l’objet Microsoft. Office. Interop. Visio. application à l’aide du champ `Application` de la classe `ThisAddIn`. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).

### <a name="document-object"></a>Objet Document
 L’objet Microsoft. Office. Interop. Visio. document est essentiel à la programmation de Visio. Il représente un fichier de dessin, de gabarit ou de modèle. Lorsque vous ouvrez un document Visio ou créez un nouveau document, vous créez un objet Microsoft. Office. Interop. Visio. document, qui est ajouté à la collection Microsoft. Office. Interop. Visio. documents de l’objet Microsoft. Office. Interop. Visio. application. .

 Le document qui a le focus est appelé le document actif. Elle est représentée par la propriété `Microsoft.Office.Interop.Visio.Application.ActiveDocument` de l’objet Microsoft. Office. Interop. Visio. application.

### <a name="page-object"></a>Page (objet)
 L’objet Microsoft. Office. Interop. Visio. page représente la zone de dessin d’une page de premier plan ou d’arrière-plan. Vous pouvez utiliser la propriété `Microsoft.Office.Interop.Visio.Page.Background` pour déterminer si une page est une page de premier plan ou d'arrière-plan.

 Pour créer des formes, vous pouvez utiliser les méthodes qui incluent les méthodes `Microsoft.Office.Interop.Visio.Page.DrawSpline` et `Microsoft.Office.Interop.Visio.Page.DrawOval`. En outre, vous pouvez récupérer des formes de base de gabarits et placer ces formes sur une page à l'aide des méthodes `Microsoft.Office.Interop.Visio.Page.Drop` ou `Microsoft.Office.Interop.Visio.Page.DropMany`.

## <a name="use-the-visio-object-model-documentation"></a>Utiliser la documentation du modèle objet Visio
 Pour obtenir des informations complètes sur le modèle objet Visio, vous pouvez vous reporter à la référence du modèle objet Visio VBA. La documentation du modèle objet VBA présente le modèle objet Visio tel qu'il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [Référence du modèle objet Visio](/office/vba/api/overview/visio/object-model).

 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA Visio. Par exemple, l’objet `Document` dans la documentation de référence du modèle objet VBA correspond au type Microsoft. Office. Interop. Visio. document dans l’assembly PIA Visio. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet de complément VSTO Visio créé à l'aide de Visual Studio.

> [!NOTE]
> À ce stade, il n'existe aucune documentation de référence pour l'assembly PIA Visio.

 Pour obtenir des exemples de code associés et des outils supplémentaires pour la création de solutions Visio, consultez le [Kit de développement logiciel](https://www.microsoft.com/download/details.aspx?id=12365)(SDK) Visio 2010.

### <a name="additional-types-in-primary-interop-assemblies"></a>Types supplémentaires dans les assemblys PIA (Primary Interop Assembly)
 Vous pouvez trouver des types dans les assemblys PIA qui ne sont pas visibles par VBA en raison des différences d'implémentation. VBA fournit une vue du modèle objet Visio qui inclut uniquement les objets et les membres que vous pouvez utiliser directement. Les assemblys PIA exposent le même modèle objet, mais incluent également les autres interfaces, classes et membres qui convertissent les objets du modèle objet COM en code managé. Ces éléments supplémentaires ne sont pas destinés à être utilisés directement dans votre code.

 Pour plus d’informations, consultez [vue d’ensemble des classes et des interfaces dans les assemblys PIA (Primary Interop Assembly) Office](/previous-versions/office/office-12/ms247299(v=office.12)) et assemblys PIA ( [Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md).

## <a name="see-also"></a>Voir aussi
- [Solutions Visio](../vsto/visio-solutions.md)
- [Utiliser des documents Visio](../vsto/working-with-visio-documents.md)
- [Utiliser des formes Visio](../vsto/working-with-visio-shapes.md)
