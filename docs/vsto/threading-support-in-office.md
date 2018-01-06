---
title: Prise en charge dans Office de thread | Documents Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2157
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c06e88c90116040fa3e9448368d32953095f889e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="threading-support-in-office"></a>Prise en charge des threads dans Office
  Cette rubrique fournit des informations sur la prise en charge des threads dans le modèle objet Microsoft Office. Le modèle objet Office n’est pas thread-safe, mais il est possible de travailler avec plusieurs threads dans une solution Office. Les applications Office sont des serveurs de modèle COM (Component Object). COM permet aux clients d’appeler des serveurs COM sur des threads arbitraires. Pour les serveurs COM qui ne sont pas thread-safe, COM fournit un mécanisme permettant de sérialiser les appels simultanés pour qu’un seul thread logique s’exécute sur le serveur à tout moment. Ce mécanisme est appelé le modèle de thread unique cloisonné (STA). Étant donné que les appels sont sérialisés, les appelants peuvent être bloqués de périodes de temps pendant que le serveur est occupé ou gère d’autres appels sur un thread d’arrière-plan.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Base de connaissances requis lors de l’utilisation de plusieurs Threads  
 Pour travailler avec plusieurs threads, vous devez disposer des connaissances de base au moins des aspects suivants du multithreading :  
  
-   API Windows  
  
-   COM concepts multithreads  
  
-   Concurrence  
  
-   Synchronisation  
  
-   marshaling  
  
 Pour obtenir des informations générales sur le multithreading, consultez [Managed Threading](/dotnet/standard/threading/).  
  
 Office s’exécute sur le STA principal. Comprendre les implications de cette permet de comprendre l’utilisation de plusieurs threads avec Office.  
  
## <a name="basic-multithreading-scenario"></a>Scénario multithread de base  
 Le code dans les solutions Office s’exécute toujours sur le thread d’interface utilisateur. Vous pouvez souhaiter lisser les performances de l’application en exécutant une tâche séparée sur un thread d’arrière-plan. L’objectif est d’effectuer deux tâches apparemment en une seule fois au lieu d’une tâche après l’autre, qui devrait harmoniser leur exécution (c’est la raison principale d’utiliser plusieurs threads). Par exemple, vous pouvez avoir votre code d’événement sur le thread d’interface utilisateur Excel principal et sur un thread d’arrière-plan, vous pouvez exécuter une tâche qui rassemble les données d’un serveur et met à jour des cellules dans l’interface utilisateur Excel avec les données à partir du serveur.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Threads d’arrière-plan qui appellent le modèle objet Office  
 Lorsqu’un thread d’arrière-plan effectue un appel à l’application Office, l’appel est marshalé automatiquement via la limite thread STA. Toutefois, il n’existe aucune garantie que l’application Office puisse gérer l’appel au moment où que le thread d’arrière-plan rend. Il existe plusieurs possibilités :  
  
1.  L’application Office doit pomper des messages pour l’appel pour avoir la possibilité d’entrer. Si elle effectue un traitement sans générant cette importante peut prendre le temps.  
  
2.  Si un autre thread logique se trouve déjà dans le cloisonnement, le nouveau thread ne peut pas entrer. Cela se produit souvent quand un thread logique entre dans l’application Office et effectue ensuite un appel réentrant à l’apartment de l’appelant. L’application est bloquée et attend qu’un appel à retourner.  
  
3.  Excel peut être dans un état de sorte qu’il ne peut pas traiter immédiatement un appel entrant. Par exemple, l’application Office peut afficher une boîte de dialogue modale.  
  
 Pour les possibilités 2 et 3, COM fournit le [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248) interface. Si le serveur l’implémente, tous les appels entrent via le [HandleIncomingCall](http://msdn.microsoft.com/en-us/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be) (méthode). Pour la possibilité 2, les appels sont automatiquement rejetés. Pour la possibilité 3, le serveur peut rejeter l’appel, selon les circonstances. Si l’appel est rejeté, l’appelant doit décider quoi faire. Normalement, l’implémente appelant [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248), auquel cas il serait notifié du rejet par le [RetryRejectedCall](http://msdn.microsoft.com/en-us/3f800819-2a21-4e46-ad15-f9594fac1a3d) (méthode).  
  
 Toutefois, dans le cas des solutions créées à l’aide des outils de développement Office dans Visual Studio, COM interop convertit tous les appels rejetés pour un <xref:System.Runtime.InteropServices.COMException> (« le filtre de message indique que l’application est occupée »). Chaque fois que vous effectuez un modèle d’objet appel sur un thread d’arrière-plan, vous devez pour être prêt à gérer cette exception. En règle générale, qui implique une nouvelle tentative pour une certaine quantité de temps, puis en affichant une boîte de dialogue. Toutefois, vous pouvez également créer le thread d’arrière-plan en tant que STA, puis enregistrez un filtre de messages pour ce thread gérer ce cas.  
  
## <a name="starting-the-thread-correctly"></a>Démarrage correct du Thread  
 Lorsque vous créez un nouveau thread STA, définissez l’état de cloisonnement sur STA avant de démarrer le thread. L'exemple de code suivant montre comment procéder.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Pour plus d’informations, consultez [Managed Threading Best Practices](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Formulaires non modales  
 Un formulaire non modal permet certain type d’interaction avec l’application pendant que le formulaire est affiché. L’utilisateur interagit avec le formulaire, et le formulaire interagit avec l’application sans fermer. Le modèle objet Office prend en charge les formulaires non modaux managés ; Toutefois, ils ne doivent pas être utilisés sur un thread d’arrière-plan.  
  
## <a name="see-also"></a>Voir aussi  
 [Threading managé](/dotnet/standard/threading/)  
 [Threads (c#)](/dotnet/csharp/programming-guide/concepts/threading/index) [threads (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Utilisation des threads et du threading](/dotnet/standard/threading/using-threads-and-threading)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  