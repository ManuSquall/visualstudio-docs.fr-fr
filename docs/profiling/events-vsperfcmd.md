---
title: "Events (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Events (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option VSPerfCmd.exe **Events** contrôle la journalisation du Suivi d'événements pour Windows \(ETW\).  Les données ETW sont enregistrées dans un fichier .etl distinct du fichier de données du profileur.  Les données peuvent être affichées dans un rapport à l'aide de la commande [VSPerfReport](../profiling/vsperfreport.md)\/summary:etw.  
  
 Vous pouvez appeler l'option **Events** à tout moment avant d'appeler la commande VSPerfCmd **Shutdown** pour arrêter le profilage.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### Paramètres  
 **On**&#124;**Off**  
 Démarre ou arrête la collecte des données d'événement.  
  
 `Guid`  
 GUID du contrôle du fournisseur.  
  
 `ProviderName`  
 Nom du fournisseur enregistré avec Windows Management Instrumentation \(WMI\).  
  
 `Flags`  
 Valeur d'indicateurs hexadécimale portant le préfixe « 0x » définie par le fournisseur d'événements.  
  
 `Level`  
 Spécifie la quantité de données collectées.  `Level` est défini par le fournisseur d'événements.  
  
 L'option **Events** interprète les mots clés de noyau suivants comme des noms de fournisseurs :  
  
 **Process**  
 Événements de processus  
  
 **Thread**  
 Événements de thread  
  
 **Image**  
 Événements de chargement et de déchargement d'images  
  
 **Disk**  
 Événements d'E\/S de disque  
  
 **File**  
 Événements d'E\/S de fichier  
  
 **Hardfault**  
 Erreurs de page matérielles  
  
 **Pagefault**  
 Erreurs de page logicielles  
  
 **Network**  
 Événements de réseau  
  
 **Registry**  
 Événements d'accès au Registre  
  
 Notez que le fournisseur du noyau peut seulement être activé.  Vous ne pouvez ni le désactiver, ni modifier ses indicateurs tant que le gestionnaire n'a pas été arrêté.  
  
## Notes  
  
> [!NOTE]
>  Lorsque les événements ETW du CLR sont activés, des données de démarrage supplémentaires sont également rassemblées dans le rapport Trace View.  Pour empêcher que des événements de démarrage apparaissent dans le rapport, utilisez la commande suivante :  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Si vous n'excluez pas les événements de démarrage, étant donné que ces événements ne sont pas répertoriés dans le fichier au format MOF \(Managed Object Format\), ils apparaissent sous forme de GUID dans le rapport.  Pour plus d'informations, consultez cette page sur le site Web Microsoft : [Exemple de fichier MOF](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)