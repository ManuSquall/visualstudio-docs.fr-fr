---
title: Threading prise en charge dans Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5aafdad425d611d7d57c2ae8e53e505d3522ba38
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871106"
---
# <a name="threading-support-in-office"></a>Threading prise en charge dans Office
  Cet article fournit des informations sur la prise en charge des threads dans le modèle d’objet Microsoft Office. Le modèle objet Office n’est pas thread-safe, mais il est possible de travailler avec plusieurs threads dans une solution Office. Les applications Office sont des serveurs de composant COM (Object Model). COM permet aux clients d’appeler des serveurs COM sur des threads arbitraires. Pour les serveurs COM qui ne sont pas thread-safe, COM fournit un mécanisme pour sérialiser les appels simultanés afin qu’un seul thread logique s’exécute sur le serveur à tout moment. Ce mécanisme est appelé le modèle de thread unique cloisonné (STA). Étant donné que les appels sont sérialisés, les appelants peuvent être bloqués pour des périodes de temps pendant que le serveur est occupé ou gère d’autres appels sur un thread d’arrière-plan.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Connaissances nécessaires à l’utilisation de plusieurs threads  
 Pour travailler avec plusieurs threads, vous devez disposer d’une connaissance élémentaire au moins des aspects suivants de multithreading :  
  
- API Windows  
  
- COM concepts multithreads  
  
- Concurrence  
  
- Synchronisation  
  
- Marshaling  
  
  Pour obtenir des informations générales sur le multithreading, consultez [threading managé](/dotnet/standard/threading/).  
  
  Office s’exécute sur le STA principal. Comprendre les implications de ce rend possible comprendre comment utiliser plusieurs threads avec Office.  
  
## <a name="basic-multithreading-scenario"></a>Scénario multithread de base  
 Le code dans les solutions Office s’exécute toujours sur le thread d’interface utilisateur principal. Vous souhaiterez peut-être aplanir les performances de l’application en exécutant une tâche distincte sur un thread d’arrière-plan. L’objectif est d’effectuer deux tâches apparemment en même temps au lieu d’une tâche après l’autre, dont le résultat dans une exécution plus lisse (c’est la raison principale d’utiliser plusieurs threads). Par exemple, vous pouvez avoir votre code d’événement sur le thread d’interface utilisateur Excel principal et sur un thread d’arrière-plan, vous pouvez exécuter une tâche qui collecte des données à partir d’un serveur et met à jour des cellules dans l’interface utilisateur Excel avec les données à partir du serveur.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Threads d’arrière-plan qui appellent le modèle d’objet Office  
 Lorsqu’un thread d’arrière-plan effectue un appel à l’application Office, l’appel est marshalé automatiquement dans les limites du mode STA. Toutefois, il n’existe aucune garantie que l’application Office puisse gérer l’appel au moment où que le thread d’arrière-plan rend. Il existe plusieurs possibilités :  
  
1. L’application Office doit pomper des messages pour l’appel de la possibilité d’entrer. Si elle fait bien nécessitant beaucoup de traitement sans donner Ceci peut prendre le temps.  
  
2. Si un autre thread logique est déjà dans le cloisonnement, le nouveau thread ne peut pas entrer. Cela se produit souvent quand un thread logique entre dans l’application Office, puis effectue un appel réentrant au cloisonnement de l’appelant. L’application est bloquée en attente pour cet appel à retourner.  
  
3. Excel se trouve peut-être dans un état où il ne peut pas gérer immédiatement un appel entrant. Par exemple, l’application Office peut afficher une boîte de dialogue modale.  
  
   Pour les possibilités 2 et 3, COM fournit le [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) interface. Si le serveur implémente, tous les appels entrent via le [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) (méthode). Possibilité 2, les appels sont automatiquement rejetés. Pour la possibilité 3, le serveur peut rejeter l’appel, selon les circonstances. Si l’appel est rejeté, l’appelant doit décider quoi faire. Normalement, l’implémente appelant [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), auquel cas il serait notifié du rejet par le [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) (méthode).  
  
   Toutefois, dans le cas de solutions créées à l’aide des outils de développement Office dans Visual Studio, COM interop convertit tous les appels rejetés à un <xref:System.Runtime.InteropServices.COMException> (« le filtre de messages indique que l’application est occupée »). Chaque fois que vous appeler un modèle d’objet sur un thread d’arrière-plan, vous devez être prêt à gérer cette exception. En règle générale, cela implique de nouvelles tentatives effectuées pendant un certain laps de temps, puis en affichant une boîte de dialogue. Toutefois, vous pouvez également créer le thread d’arrière-plan comme STA et puis inscrire un filtre de messages pour ce thread afin de gérer ce cas.  
  
## <a name="start-the-thread-correctly"></a>Démarrer le thread correctement  
 Lorsque vous créez un nouveau thread STA, définissez l’état de cloisonnement sur STA avant de démarrer le thread. L'exemple de code suivant montre comment procéder.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Pour plus d’informations, consultez [meilleures pratiques pour le threading managé](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Formulaires sans mode  
 Un formulaire non modal permet certain type d’interaction avec l’application tandis que le formulaire s’affiche. L’utilisateur interagit avec le formulaire, et le formulaire interagit avec l’application sans fermer. Le modèle objet Office prend en charge les formulaires sans mode gérés ; Toutefois, ils ne doivent pas utilisés sur un thread d’arrière-plan.  
  
## <a name="see-also"></a>Voir aussi  
 [Threading managé](/dotnet/standard/threading/)  
 [Threads (c#)](/dotnet/csharp/programming-guide/concepts/threading/index) [threads (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Utilisez threads et threading](/dotnet/standard/threading/using-threads-and-threading)   
 [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  