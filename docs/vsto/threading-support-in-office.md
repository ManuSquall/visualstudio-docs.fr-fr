---
title: Prise en charge des threads dans Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3218a12add86739c76cd50f82fdda5d845e2b069
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62978765"
---
# <a name="threading-support-in-office"></a>Prise en charge des threads dans Office
  Cet article fournit des informations sur la prise en charge des threads dans le modèle objet Microsoft Office. Le modèle objet Office n’est pas thread-safe, mais il est possible d’utiliser plusieurs threads dans une solution Office. Les applications Office sont des serveurs COM (Component Object Model). COM permet aux clients d’appeler des serveurs COM sur des threads arbitraires. Pour les serveurs COM qui ne sont pas thread-safe, COM fournit un mécanisme pour sérialiser les appels simultanés afin qu’un seul thread logique s’exécute sur le serveur à tout moment. Ce mécanisme est connu sous le nom de modèle STA (Single-Threaded Apartment). Étant donné que les appels sont sérialisés, les appelants peuvent être bloqués pendant des périodes de temps, alors que le serveur est occupé ou gère d’autres appels sur un thread d’arrière-plan.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Connaissances requises lors de l’utilisation de plusieurs threads
 Pour travailler avec plusieurs threads, vous devez avoir au moins une connaissance de base des aspects suivants du Multithreading :

- API Windows

- Concepts COM multithread

- Accès concurrentiel

- Synchronisation

- Marshaling

  Pour obtenir des informations générales sur le multithreading, consultez [threads managés](/dotnet/standard/threading/).

  Office s’exécute dans le STA principal. En comprenant les implications de cette opération, il est possible de comprendre comment utiliser plusieurs threads avec Office.

## <a name="basic-multithreading-scenario"></a>Scénario de traitement multithread de base
 Le code dans les solutions Office s’exécute toujours sur le thread d’interface utilisateur principal. Vous souhaiterez peut-être lisser les performances de l’application en exécutant une tâche distincte sur un thread d’arrière-plan. L’objectif est de réaliser deux tâches apparemment à la fois au lieu d’une tâche suivie de l’autre, ce qui devrait entraîner une exécution plus lisse (la principale raison d’utiliser plusieurs threads). Par exemple, vous pouvez avoir votre code d’événement sur le thread d’interface utilisateur Excel principal et, sur un thread d’arrière-plan, vous pouvez exécuter une tâche qui recueille des données à partir d’un serveur et met à jour les cellules de l’interface utilisateur Excel avec les données du serveur.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Threads d’arrière-plan qui appellent le modèle d’objet Office
 Quand un thread d’arrière-plan effectue un appel à l’application Office, l’appel est marshalé automatiquement à travers la limite STA. Toutefois, il n’y a aucune garantie que l’application Office peut gérer l’appel au moment où le thread d’arrière-plan le fait. Il existe plusieurs possibilités :

1. L’application Office doit pomper les messages pour que l’appel ait la possibilité d’entrer. S’il s’agit d’un traitement lourd sans entraîner cette opération peut prendre du temps.

2. Si un autre thread logique figure déjà dans le cloisonnement, le nouveau thread ne peut pas entrer. Cela se produit souvent lorsqu’un thread logique accède à l’application Office, puis fait un rappel réentrant au cloisonnement de l’appelant. L’application est bloquée en attendant que cet appel retourne.

3. Excel peut être dans un état tel qu’il ne peut pas gérer immédiatement un appel entrant. Par exemple, l’application Office peut afficher une boîte de dialogue modale.

   Pour les possibilités 2 et 3, COM fournit l’interface [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) . Si le serveur le met en œuvre, tous les appels passent par la méthode [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) . Pour la deuxième possibilité, les appels sont automatiquement rejetés. Pour la possibilité 3, le serveur peut rejeter l’appel, selon les circonstances. Si l’appel est rejeté, l’appelant doit décider de la procédure à suivre. Normalement, l’appelant implémente [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), auquel cas il est notifié du rejet par la méthode [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) .

   Toutefois, dans le cas des solutions créées à l’aide des outils de développement Office dans Visual Studio, COM Interop convertit tous les appels rejetés en un <xref:System.Runtime.InteropServices.COMException> (« le filtre de message indique que l’application est occupée »). Chaque fois que vous effectuez un appel de modèle objet sur un thread d’arrière-plan, vous devez être prêt à gérer cette exception. En général, cela implique une nouvelle tentative pendant un certain laps de temps, puis l’affichage d’une boîte de dialogue. Toutefois, vous pouvez également créer le thread d’arrière-plan en tant que STA, puis inscrire un filtre de messages pour que ce thread gère ce cas.

## <a name="start-the-thread-correctly"></a>Démarrer le thread correctement
 Quand vous créez un thread STA, affectez à l’état de cloisonnement la valeur STA avant de démarrer le thread. L'exemple de code suivant montre comment procéder.

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 Pour plus d’informations, consultez [meilleures pratiques pour le threading managé](/dotnet/standard/threading/managed-threading-best-practices).

## <a name="modeless-forms"></a>Formulaires non modals
 Un formulaire non modal autorise un certain type d’interaction avec l’application pendant que le formulaire est affiché. L’utilisateur interagit avec le formulaire et le formulaire interagit avec l’application sans se fermer. Le modèle objet Office prend en charge les formulaires non managés managés ; Toutefois, ils ne doivent pas être utilisés sur un thread d’arrière-plan.

## <a name="see-also"></a>Voir aussi
- [Threads (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [Threads (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [Utiliser des threads et des threads](/dotnet/standard/threading/using-threads-and-threading)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
