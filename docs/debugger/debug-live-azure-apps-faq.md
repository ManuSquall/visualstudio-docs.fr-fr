---
title: Questions fréquentes (FAQ) sur le débogage d’instantané | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 315b24d384a1e3576af6590923c0e546785918ae
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67255980"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Questions fréquentes sur le débogage d’instantané dans Visual Studio

Voici une liste de questions qui peuvent survenir lors du débogage d’applications Azure en production à l’aide du Débogueur de capture instantanée.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Quel est le coût en matière de performances de la prise d’un instantané ?

Lorsque le Débogueur de capture instantanée capture un instantané de votre application, il duplique (fork) le processu de l’application et interrompt la copie dupliquée. Lorsque vous déboguez un instantané, vous déboguez sur la copie dupliquée du processus. Ce processus ne prend que 10 à 20 millisecondes, mais ne copie pas le tas complet de l’application. À la place, il copie uniquement la table des pages et définit les pages sur « copie pour écriture ». Si certains des objets de votre application sur la pile changent, leurs pages correspondantes sont alors copiées. C’est pourquoi chaque capture instantanée a un petit coût en mémoire (de l’ordre de centaines de kilo-octets pour la plupart des applications).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Que se passe-t-il si j’ai un Azure App Service scaled-out (plusieurs instances de mon application) ?

Lorsque vous avez plusieurs instances de votre application, les snappoints sont appliqués à chaque instance unique. Seul le premier snappoint à atteindre les conditions spécifiées crée un instantané. Si vous avez plusieurs snappoints, les instantanés ultérieurs proviennent de l’instance qui a créé le premier instantané. Les logpoints envoyés à la fenêtre de sortie affichent uniquement les messages d’une instance, tandis que les logpoints envoyés aux journaux d’application envoient des messages à partir de chaque instance.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Comment le Débogueur de capture instantanée charge-t-il des symboles ?

Le Débogueur de capture instantanée nécessite que vous ayez les symboles correspondants pour votre application de manière locale ou déployée sur votre Azure App Service. (Les PDB incorporés ne sont actuellement pas pris en charge.) Le Débogueur de capture instantanée télécharge automatiquement les symboles à partir de votre Azure App Service. À partir de Visual Studio 2017 version 15.2, le déploiement sur Azure App Service déploie également les symboles de votre application.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Le Débogueur de capture instantanée fonctionne-t-il avec les builds de publication de mon application ?

Oui. Le Débogueur de capture instantanée est prévu pour fonctionner sur les builds de publication. Lorsqu’un snappoint est placé dans une fonction, la fonction est recompilée dans une version de débogage, pour la rendre compatible avec le débogage. L’arrêt du Débogueur de capture instantanée restaure les fonctions sur la build de publication.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Les logpoints peuvent-ils provoquer des effets secondaires dans mon application de production ?

Non. Les messages de journal que vous ajoutez à votre application sont évalués de manière virtuelle. Ils ne peuvent pas causer d’effets secondaires dans votre application. Toutefois, certaines propriétés natives peuvent ne pas être accessibles avec les logpoints.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Le Débogueur de capture instantanée fonctionne-t-il si mon serveur est en charge ?

Oui, le débogage d’instantané peut fonctionner pour les serveurs en charge. Le Débogueur de capture instantanée limite et ne capture pas les instantanés en cas de faible quantité de mémoire disponible sur votre serveur.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Comment désinstaller le Débogueur de capture instantanée ?

Vous pouvez désinstaller l’extension de site du Débogueur de capture instantanée sur votre App Service en procédant comme suit :

1. Désactiver votre App Service via Cloud Explorer dans Visual Studio ou le portail Azure.
1. Accédez au site Kudu de votre App Service (autrement dit, yourappservice.**scm**.azurewebsites.net) et accédez à **Extensions de site**.
1. Cliquez sur le X de l’extension de site du Débogueur de capture instantanée pour le supprimer.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Pourquoi les ports sont-ils ouverts pendant une session du Débogueur de capture instantanée ?

Le Débogueur de capture instantanée doit ouvrir un ensemble de ports pour déboguer les instantanés pris dans Azure, ce sont les mêmes ports requis pour le débogage distant. [Vous trouverez la liste des ports ici](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Comment désactiver l’extension du débogueur distant ?

Pour les Services d’application :
1. Désactiver l’extension de débogueur distant via le portail Azure pour votre App Service.
2. Portail Azure > Panneau de ressources de votre Service d’Application > *paramètres d’Application*
3. Accédez à la *débogage* section et cliquez sur le *hors* bouton *le débogage à distance*.

Pour AKS :
1. Mettre à jour votre fichier Dockerfile pour supprimer les sections correspondant à la [Visual Studio Snapshot Debugger sur les images Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Régénérez et redéployez l’image Docker modifiée.

Pour la mise à l’échelle de machine virtuelle/machine virtuelle jeux supprimer les pools KeyVaults et NAT de trafic entrant d’extension, certificats, débogueur distant comme suit :

1. Supprimer l’extension du débogueur distant  

   Il existe plusieurs façons de désactiver le débogueur distant pour les machines virtuelles et des machines virtuelles identiques :  

      - Désactiver le débogueur distant via Cloud Explorer  

         - Cloud Explorer > votre ressource de machine virtuelle > désactiver le débogage (la désactivation de débogage est inexistant pour machines virtuelles identiques sur le Cloud Explorer).  


      - Désactiver le débogueur distant avec Scripts/applets de commande PowerShell  

         Pour la machine virtuelle :  

         ```
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  
         ```

         Pour les machines virtuelles identiques :  
         ```
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName  
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name  
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension  
         ```

      - Désactiver le débogueur distant via le portail Azure
         - Portail Azure > votre groupe identique de machine virtuelle/machine virtuelle définit le panneau de ressources > Extensions  
         - Désinstaller l’extension Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  


         > [!NOTE]
         > Machines virtuelles identiques - le portail n’autorise pas supprimer les ports DebuggerListener. Vous devez utiliser Azure PowerShell. Pour plus d'informations, consultez ce qui suit.
  
2. Supprimer des certificats et Azure Key Vault

   Lorsque vous installez l’extension de débogueur distant pour la machine virtuelle ou des machines virtuelles identiques, les certificats de client et serveur sont créés pour authentifier le client Visual Studio avec la Machine virtuelle Azure/ressources de machines virtuelles identiques.  

   - Le certificat Client  

      Ce certificat est un certificat auto-signé situé dans Cert : / CurrentUser/My /  

      ```
      Thumbprint                                Subject  
      ----------                                -------  

      1234123412341234123412341234123412341234  CN=ResourceName  
      ```

      La première consiste à supprimer ce certificat à partir de votre ordinateur par le biais de PowerShell

      ```
      $ResourceName = 'ResourceName' # from above  
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item  
      ```

   - Le certificat de serveur
      - L’empreinte de certificat de serveur correspondante est déployé en tant que secret au coffre de clés Azure. Visual Studio va tenter de trouver ou créer un coffre de clés avec le préfixe MSVSAZ * dans la région correspondant à la machine virtuelle ou ressources de machines virtuelles identiques. Identiques de machine virtuelle ou une machine virtuelle toutes les ressources déployées dans cette région seront par conséquent partagent le même coffre de clés.  
      - Pour supprimer le secret d’empreinte de certificat de serveur, accédez au portail Azure et recherchez le coffre de clés MSVSAZ * dans la même région qui héberge votre ressource. Supprimer la clé secrète qui doit être étiquetée `remotedebugcert<<ResourceName>>`  
      - Vous devez également supprimer le secret de serveur à partir de votre ressource via PowerShell.  

      Pour les machines virtuelles :  

      ```
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVM -ResourceGroupName $rgName -VM $vm  
      ```
                        
      Pour les machines virtuelles identiques :  

      ```
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss  
      ```
                        
3. Supprimez tous les pools NAT de trafic entrant DebuggerListener (machines virtuelles identiques uniquement)  

   Le débogueur distant introduit les pools NAT DebuggerListener entrantes qui sont appliqués à l’équilibreur de charge de votre groupe identique.  

   ```
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools  
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
                
   if ($LoadBalancerName)  
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName  
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
      Set-AzLoadBalancer -LoadBalancer $lb  
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Comment désactiver le débogueur de capture instantanée ?

Pour App Service :
1. Désactiver le débogueur de capture instantanée via le portail Azure pour votre App Service.
2. Portail Azure > Panneau de ressources de votre Service d’Application > *paramètres d’Application*
3. Supprimer les paramètres d’application suivants dans le portail Azure et enregistrez vos modifications. 
    - INSTRUMENTATIONENGINE_EXTENSION_VERSION
    - SNAPSHOTDEBUGGER_EXTENSION_VERSION

    > [!WARNING]
    > Les modifications apportées aux paramètres de l’Application lance un redémarrage de l’application. Pour plus d’informations sur les paramètres de l’Application, consultez [configurer une application app Service dans le portail Azure](/azure/app-service/web-sites-configure).

Pour AKS :
1. Mettre à jour votre fichier Dockerfile pour supprimer les sections correspondant à la [Visual Studio Snapshot Debugger sur les images Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Régénérez et redéployez l’image Docker modifiée.

Pour les jeux de mise à l’échelle machine virtuelle/machine virtuelle :

Il existe plusieurs façons de désactiver le débogueur de capture instantanée :
- Cloud Explorer > votre machine virtuelle/machine virtuelle identiques ressource > désactiver les Diagnostics

- Portail Azure > votre machine virtuelle/machine virtuelle identiques Panneau de ressources > Extensions > Microsoft.Insights.VMDiagnosticsSettings désinstaller extension

- Applets de commande PowerShell [Az PowerShell](https://docs.microsoft.com/powershell/azure/overview)

    Machine virtuelle :
    ```
        Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings 
    ```
    
    Machines virtuelles identiques :
    ```
        $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
        Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
    ```

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.md)
- [Déboguer des applications ASP.NET en production à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-applications.md)
- [Déboguer des ensembles de mise à l’échelle des Machines Machines\Virtual virtuel ASP.NET Azure en direct à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-virtual-machines.md)
- [Déboguer ASP.NET Azure Kubernetes en direct à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-kubernetes.md)
- [Problèmes connus et dépannage pour le débogage d’instantané](../debugger/debug-live-azure-apps-troubleshooting.md)