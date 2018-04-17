---
title: 'Comment : utiliser le journal d’activité | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6200c5e71054c6132d9239769d354bfd32703fb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-activity-log"></a>Comment : utiliser le journal d’activité
Les VSPackages peuvent écrire des messages dans le journal d’activité. Cette fonctionnalité est particulièrement utile pour déboguer les VSPackages dans les environnements de vente au détail.  
  
> [!TIP]
>  Le journal d’activité est toujours activé. Visual Studio conserve un tampon propagée des 100 dernières entrées, ainsi que les 10 premières entrées, qui présentent des informations de configuration générale.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Pour écrire une entrée dans le journal d’activité  
  
1.  Insérez ce code dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode ou dans toute autre méthode sauf dans le constructeur de VSPackage :  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Ce code obtient le <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de service et le caste vers une <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> écrit une entrée d’information dans le journal des activités en utilisant le contexte de la culture actuels.  
  
2.  Lorsque le VSPackage est chargé (généralement lorsqu’une commande est appelée ou une fenêtre est ouverte), le texte est écrit dans le journal d’activité.  
  
### <a name="to-examine-the-activity-log"></a>Examinez le journal d’activité  
  
1.  Exécutez Visual Studio avec le [/journaux](../ide/reference/log-devenv-exe.md) commutateur de ligne de commande pour écrire ActivityLog.xml sur le disque pendant votre session.

2.  Après la fermeture de Visual Studio, recherchez le journal d’activité dans le sous-dossier pour les données de Visual Studio : *%AppData%*\Microsoft\VisualStudio\15.0\ActivityLog.xml.  
  
3.  Ouvrez le journal d’activité avec n’importe quel éditeur de texte. Voici une entrée de type :  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programmation fiable  
 Étant donné que le journal d’activité est un service, le journal d’activité n’est pas disponible dans le constructeur du VSPackage.  
  
 Vous devez obtenir le journal d’activité juste avant l’écriture dans celle-ci. Ne pas mettre en cache ou enregistrer le journal d’activité pour une utilisation ultérieure.  
  
## <a name="see-also"></a>Voir aussi
 [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Dépanner les packages VS](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
