---
title: Events (VSPerfCmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4aa07333385951ba2ffd2f1bcf86aa5e8442982
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
L’option **Events** de VSPerfCmd.exe contrôle la journalisation du suivi d’événements pour Windows (ETW). Les données ETW sont enregistrées dans un fichier .etl, qui est distinct du fichier de données du profileur. Les données peuvent être affichées dans un rapport avec la commande [VSPerfReport](../profiling/vsperfreport.md) /summary:etw.  
  
 L’option **Events** peut être appelée à tout moment avant que la commande VSPerfCmd **Shutdown** soit appelée pour arrêter le profilage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Paramètres  
 **On**&#124;**Off**  
 Démarre ou arrête la collecte des données d’événement.  
  
 `Guid`  
 GUID du contrôle fournisseur.  
  
 `ProviderName`  
 Nom du fournisseur qui est inscrit auprès de Windows Management Instrumentation (WMI).  
  
 `Flags`  
 Valeur des indicateurs préfixée de « 0x » qui est définie par le fournisseur d’événements.  
  
 `Level`  
 Spécifie la quantité de données collectées. `Level` est défini par le fournisseur d’événements.  
  
 L’option **Events** interprète les mots clés suivants du noyau comme des noms de fournisseurs :  
  
 **Process**  
 Événements de processus  
  
 **Thread**  
 Événements de thread  
  
 **Image**  
 Événements de chargement et de déchargement d’image  
  
 **Disk**  
 Événements d’E/S de disque  
  
 **Fichier**  
 Événements d’E/S de fichier  
  
 **Hardfault**  
 Défauts de pages matériels  
  
 **Pagefault**  
 Défauts de pages logiciels  
  
 **Network**  
 Événements réseau  
  
 **Registry**  
 Événements d’accès au Registre  
  
 Notez que le fournisseur de noyau peut être seulement activé. Il ne peut pas être désactivé et ses indicateurs ne peuvent pas être modifiés jusqu’à l’arrêt du moniteur.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Quand des événements ETW du CLR sont activés, des données de démarrage supplémentaires sont également collectées dans le rapport Vue Trace. Pour exclure les événements de démarrage du rapport, utilisez la commande suivante :  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Si vous n’excluez pas les événements de démarrage, comme ces événements ne sont pas listés dans le fichier MOF (Managed Object Format), ils apparaissent sous forme de GUID dans le rapport. Pour plus d’informations, consultez cette page sur le site web de Microsoft : [Exemple de fichier MOF (Managed Object Format)](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)