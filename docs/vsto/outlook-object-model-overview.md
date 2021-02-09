---
title: Vue d’ensemble du modèle objet Outlook
description: Découvrez comment vous pouvez interagir avec les objets fournis par le modèle objet Outlook pour développer des compléments VSTO pour Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 316ead76be1f84fccc6f675b204587008e8a194a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885298"
---
# <a name="outlook-object-model-overview"></a>Vue d’ensemble du modèle objet Outlook
  Pour développer des compléments VSTO pour Microsoft Office Outlook, vous pouvez interagir avec les objets fournis par le modèle objet Outlook. Le modèle objet Outlook fournit des classes et des interfaces qui représentent des éléments dans l'interface utilisateur. Par exemple, l'objet <xref:Microsoft.Office.Interop.Outlook.Application> représente l'application entière, l'objet <xref:Microsoft.Office.Interop.Outlook.Folder> représente un dossier qui contient des messages électroniques ou d'autres éléments, et l'objet <xref:Microsoft.Office.Interop.Outlook.MailItem> représente un message électronique.

 Cette rubrique fournit une brève présentation de certains objets principaux du modèle objet Outlook. Pour obtenir des ressources qui vous permettent d’en savoir plus sur l’ensemble du modèle objet Outlook, consultez [utiliser la documentation du modèle objet Outlook](#refdoc).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-objects-in-an-outlook-project"></a>Accéder aux objets dans un projet Outlook
 Outlook fournit de nombreux objets avec lesquels vous pouvez interagir. Pour utiliser le modèle objet efficacement, vous devez être familiarisé avec les objets de niveau supérieur suivants :

- <xref:Microsoft.Office.Interop.Outlook.Application>

- <xref:Microsoft.Office.Interop.Outlook.Explorer>

- <xref:Microsoft.Office.Interop.Outlook.Inspector>

- <xref:Microsoft.Office.Interop.Outlook.Folder>

- <xref:Microsoft.Office.Interop.Outlook.MailItem>

- <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>

- <xref:Microsoft.Office.Interop.Outlook.TaskItem>

- <xref:Microsoft.Office.Interop.Outlook.ContactItem>

### <a name="application-object"></a>Objet application
 L'objet <xref:Microsoft.Office.Interop.Outlook.Application> représente l'application Outlook. Il s'agit de l'objet de niveau supérieur le plus élevé dans le modèle objet Outlook. Voici quelques-uns des membres les plus importants de cet objet :

- la méthode [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) , qui vous permet de créer un élément tel qu'un message électronique, une tâche ou un rendez-vous ;

- la propriété <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> , qui vous permet d'accéder aux fenêtres affichant le contenu d'un dossier dans l'interface utilisateur d'Outlook ;

- la propriété <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> , qui vous permet d'accéder aux fenêtres affichant le contenu d'un élément unique, par exemple un message électronique ou une demande de réunion.

  Pour récupérer une instance de l' <xref:Microsoft.Office.Interop.Outlook.Application> objet, utilisez le champ application de la `ThisAddIn` classe dans votre projet. Pour plus d’informations, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

> [!NOTE]
> Pour éviter les avertissements de sécurité quand vous utilisez des propriétés et des méthodes qui sont bloquées par le module de protection du modèle objet Outlook, récupérez des objets Outlook à partir du champ application de la `ThisAddIn` classe. Pour plus d’informations, consultez [considérations de sécurité spécifiques pour les solutions Office](../vsto/specific-security-considerations-for-office-solutions.md).

### <a name="explorer-object"></a>Objet Explorer
 L'objet <xref:Microsoft.Office.Interop.Outlook.Explorer> représente une fenêtre qui affiche le contenu d'un dossier comprenant des éléments tels que des messages électroniques, des tâches ou des rendez-vous. L'objet <xref:Microsoft.Office.Interop.Outlook.Explorer> inclut les méthodes et propriétés que vous pouvez utiliser pour modifier la fenêtre, ainsi que les événements qui sont déclenchés quand la fenêtre change.

 Pour obtenir un objet <xref:Microsoft.Office.Interop.Outlook.Explorer> , effectuez l'une des opérations suivantes :

- Utilisez la propriété <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> de l'objet <xref:Microsoft.Office.Interop.Outlook.Application> pour accéder à tous les objets <xref:Microsoft.Office.Interop.Outlook.Explorer> dans Outlook.

- Utilisez la méthode <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> de l'objet <xref:Microsoft.Office.Interop.Outlook.Application> pour obtenir le <xref:Microsoft.Office.Interop.Outlook.Explorer> qui possède actuellement le focus.

- Utilisez la méthode `GetExplorer` de l’objet <xref:Microsoft.Office.Interop.Outlook.Folder> pour obtenir le <xref:Microsoft.Office.Interop.Outlook.Explorer> du dossier actif.

### <a name="inspector-object"></a>Objet Inspector
 L'objet <xref:Microsoft.Office.Interop.Outlook.Inspector> représente une fenêtre qui affiche un élément unique, par exemple un message électronique, une tâche ou un rendez-vous. L'objet <xref:Microsoft.Office.Interop.Outlook.Inspector> inclut les méthodes et propriétés que vous pouvez utiliser pour modifier la fenêtre, ainsi que les événements qui sont déclenchés quand la fenêtre change.

 Pour obtenir un objet <xref:Microsoft.Office.Interop.Outlook.Inspector> , effectuez l'une des opérations suivantes :

- Utilisez la propriété <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> de l'objet <xref:Microsoft.Office.Interop.Outlook.Application> pour accéder à tous les objets <xref:Microsoft.Office.Interop.Outlook.Inspector> dans Outlook.

- Utilisez la méthode <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> de l'objet <xref:Microsoft.Office.Interop.Outlook.Application> pour obtenir le <xref:Microsoft.Office.Interop.Outlook.Inspector> qui possède actuellement le focus.

- Utilisez la méthode `GetInspector` d'un élément spécifique, par exemple <xref:Microsoft.Office.Interop.Outlook.MailItem> ou <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, pour récupérer l'inspecteur associé.

### <a name="folder-object"></a>Objet Folder
 L'objet <xref:Microsoft.Office.Interop.Outlook.Folder> représente un dossier qui contient les messages électroniques, les contacts, les tâches et d'autres éléments. Outlook fournit 16 objets <xref:Microsoft.Office.Interop.Outlook.Folder> par défaut.

 Les objets <xref:Microsoft.Office.Interop.Outlook.Folder> par défaut sont définis par les valeurs d'énumération <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> . Par exemple,

 Microsoft. Office. Interop. Outlook. OlDefaultFolders. olFolderInbox correspond au dossier **boîte de réception** dans Outlook.

 Pour obtenir un exemple qui montre comment accéder à un par défaut <xref:Microsoft.Office.Interop.Outlook.Folder> et créer un nouveau <xref:Microsoft.Office.Interop.Outlook.Folder> , consultez Guide pratique [pour créer des éléments de dossier personnalisés par programmation](../vsto/how-to-programmatically-create-custom-folder-items.md).

### <a name="mailitem-object"></a>Objet MailItem
 L'objet <xref:Microsoft.Office.Interop.Outlook.MailItem> représente un message électronique. Les objets<xref:Microsoft.Office.Interop.Outlook.MailItem> se trouvent généralement dans des dossiers, par exemple **Boîte de réception**, **Éléments envoyés** et **Boîte d'envoi**. <xref:Microsoft.Office.Interop.Outlook.MailItem> expose les propriétés et méthodes qui peuvent être utilisées pour créer et envoyer des messages électroniques.

 Pour obtenir un exemple qui montre comment créer un message électronique, consultez [Comment : créer un élément de messagerie par programmation](../vsto/how-to-programmatically-create-an-e-mail-item.md).

### <a name="appointmentitem-object"></a>Objet AppointmentItem
 L'objet <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> représente une réunion, un rendez-vous unique, ou un rendez-vous ou une réunion périodique, dans le dossier **Calendrier** . L'objet <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> inclut des méthodes qui effectuent des actions telles que répondre à des demandes de réunion ou les transférer, ainsi que des propriétés qui spécifient les détails de la réunion, par exemple le lieu et l'heure.

 Pour obtenir un exemple qui montre comment créer un rendez-vous, consultez Guide pratique [pour créer une demande de réunion par programmation](../vsto/how-to-programmatically-create-a-meeting-request.md).

### <a name="taskitem-object"></a>TaskItem, objet
 L'objet <xref:Microsoft.Office.Interop.Outlook.TaskItem> représente une tâche à exécuter dans un laps de temps spécifique. Les objets<xref:Microsoft.Office.Interop.Outlook.TaskItem> se trouvent dans le dossier **Tâches** .

 Pour créer une tâche, utilisez la méthode [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) de l'objet <xref:Microsoft.Office.Interop.Outlook.Application> , puis passez la valeur <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> pour le paramètre.

### <a name="contactitem-object"></a>Objet ContactItem
 L'objet <xref:Microsoft.Office.Interop.Outlook.ContactItem>représente un contact dans le dossier **Contacts** . Les objets<xref:Microsoft.Office.Interop.Outlook.ContactItem> contiennent diverses informations de contact pour les personnes qu'ils représentent, par exemple des adresses postales, des adresses de messagerie et des numéros de téléphone.

 Pour obtenir un exemple qui montre comment créer un contact, consultez [Comment : ajouter une entrée à des contacts Outlook par programmation](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Pour obtenir un exemple qui montre comment rechercher un contact existant, consultez [Comment : Rechercher un contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md).

## <a name="use-the-outlook-object-model-documentation"></a><a name="refdoc"></a> Utiliser la documentation du modèle objet Outlook
 Pour obtenir des informations complètes sur le modèle objet Outlook, vous pouvez consulter la documentation de référence de l'assembly PIA (Primary Interop Assembly) Outlook et la documentation de référence du modèle objet VBA.

### <a name="primary-interop-assembly-reference"></a>Référence d’assembly PIA (Primary Interop Assembly)
 La documentation de référence de l'assembly PIA Outlook décrit les types des assemblys PIA (Primary Interop Assembly) pour Outlook 2010. Pour plus d’informations, consultez Référence de l' [assembly PIA (Primary Interop Assembly) Outlook 2010](/previous-versions/office/developer/office-2010/bb652780(v=office.14)).

 Outre la fourniture d'informations sur tous les types des assemblys PIA (Primary Interop Assembly), cette documentation propose également des informations supplémentaires sur la structure des assemblys PIA (Primary Interop Assembly), ainsi que des exemples de code pour les tâches courantes basées sur la technologie Automation dans Outlook.

### <a name="vba-object-model-reference"></a>Référence du modèle objet VBA
 La documentation de référence du modèle objet VBA présente le modèle objet Outlook tel qu'il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [Référence du modèle objet Outlook 2010](/office/vba/api/overview/Outlook/object-model).

 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA Outlook. Par exemple, l’objet Inspector dans la documentation de référence du modèle objet VBA correspond à l' <xref:Microsoft.Office.Interop.Outlook.Inspector> objet dans l’assembly PIA Outlook. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans la documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet de complément Outlook VSTO créé à l'aide de Visual Studio.

### <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Utiliser des éléments de contact](../vsto/working-with-contact-items.md)|Fournit des rubriques qui montrent comment effectuer des tâches avec des contacts.|
|[Utiliser des éléments de messagerie](../vsto/working-with-mail-items.md)|Fournit des rubriques qui montrent comment effectuer des tâches avec des éléments de messagerie.|
|[Utiliser des dossiers](../vsto/working-with-folders.md)|Fournit des rubriques qui montrent comment effectuer des tâches avec des dossiers.|
|[Utiliser des éléments de calendrier](../vsto/working-with-calendar-items.md)|Fournit des rubriques qui montrent comment effectuer des tâches avec des éléments du calendrier.|
|[Comment : déterminer l’élément Outlook actuel par programmation](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Montre comment afficher le nom du dossier actuel, ainsi que certaines informations sur l'élément sélectionné.|
