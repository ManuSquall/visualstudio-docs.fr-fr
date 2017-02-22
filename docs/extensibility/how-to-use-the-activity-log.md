---
title: "Comment&#160;: utiliser le journal d’activit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, débogage"
  - "VSPackages, résolution des problèmes"
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Comment&#160;: utiliser le journal d’activit&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages peuvent écrire des messages dans le journal d’activité. Cette fonctionnalité est particulièrement utile pour déboguer les VSPackages dans les environnements de vente au détail.  
  
> [!TIP]
>  Le journal d’activité est toujours activé. Visual Studio conserve un tampon de substitution des entrées dernière cent ainsi que les dix premières entrées, qui présentent des informations de configuration générales.  
  
### Pour écrire une entrée dans le journal d’activité  
  
1.  Insérez ce code dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode ou dans toute autre méthode sauf le constructeur VSPackage :  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Ce code obtient le <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de service et le caste en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface.<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> écrit une entrée d’information dans le journal d’activité en utilisant le contexte de la culture actuels.  
  
2.  Lors du chargement du package VS \(généralement lorsqu’une commande est appelée ou une fenêtre est ouverte\), le texte est écrit dans le journal d’activité.  
  
### Examinez le journal d’activité  
  
1.  Rechercher le journal d’activité dans le sous\-dossier de données de Visual Studio : *%appdata%*\\Microsoft\\VisualStudio\\14.0\\ActivityLog.XML...  
  
2.  Ouvrez le journal d’activité avec n’importe quel éditeur de texte. Voici une entrée habituelle :  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## Programmation fiable  
 Étant donné que le journal d’activité est un service, le journal d’activité n’est pas disponible dans le constructeur VSPackage.  
  
 Vous devez obtenir le journal d’activité juste avant l’écriture dans celle\-ci. Ne pas mettre en cache ou enregistrer le journal d’activité pour une utilisation ultérieure.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Dépanner les packages VS](../extensibility/troubleshooting-vspackages.md)   
 [Packages VS](../extensibility/internals/vspackages.md)