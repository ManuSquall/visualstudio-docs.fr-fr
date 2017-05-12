---
title: "Comment : utiliser le journal d’activité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c9df048a49580f3526b48e29041ef3758722ed27
ms.openlocfilehash: dc821f22a04432989a2edb68c483d298ffcf0eb7
ms.lasthandoff: 05/03/2017

---
# <a name="how-to-use-the-activity-log"></a>Comment : utiliser le journal d’activité
Les VSPackages peuvent écrire des messages dans le journal d’activité. Cette fonctionnalité est particulièrement utile pour déboguer les VSPackages dans les environnements de vente au détail.  
  
> [!TIP]
>  Le journal d’activité est toujours activé. Visual Studio conserve un tampon propagée de celui dernières entrées, ainsi que les entrées de dix premières, qui présentent des informations de configuration générale.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Pour écrire une entrée dans le journal d’activité  
  
1.  Insérez ce code dans la méthode < xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A > ou toute autre méthode sauf dans le constructeur de VSPackage :  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Ce code obtient le service < xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog > et de le convertir en une interface de < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog >. < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A > écrit une entrée d’information dans le journal des activités en utilisant le contexte de la culture actuels.  
  
2.  Lorsque le VSPackage est chargé (généralement lorsqu’une commande est appelée ou une fenêtre est ouverte), le texte est écrit dans le journal d’activité.  
  
### <a name="to-examine-the-activity-log"></a>Examinez le journal d’activité  
  
1.  Rechercher le journal d’activité dans le sous-dossier de données de Visual Studio : *%AppData%*\Microsoft\VisualStudio\15.0\ActivityLog.XML...  
  
2.  Ouvrez le journal d’activité avec n’importe quel éditeur de texte. Voici une entrée de type :  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programmation fiable  
 Étant donné que le journal d’activité est un service, le journal d’activité n’est pas disponible dans le constructeur du VSPackage.  
  
 Vous devez obtenir le journal d’activité juste avant l’écriture dans celle-ci. Ne pas mettre en cache ou enregistrer le journal d’activité pour une utilisation ultérieure.  
  
## <a name="see-also"></a>Voir aussi  
 < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog >   
 < xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE >   
 [Dépanner les packages VS](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)

