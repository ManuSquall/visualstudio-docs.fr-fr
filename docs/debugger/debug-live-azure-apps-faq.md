---
title: Questions fréquentes (FAQ) sur le débogage d’instantané | Microsoft Docs
description: Consultez la liste des questions fréquemment posées (FAQ) qui peuvent survenir lors du débogage d’applications Azure en direct à l’aide du Débogueur de capture instantanée dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9bd8a80f7f6d11587c9f0cd5c6b9bf96e38a0a74
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800502"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Questions fréquentes sur le débogage d’instantané dans Visual Studio

Voici une liste de questions qui peuvent survenir lors du débogage d’applications Azure en production à l’aide du Débogueur de capture instantanée.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Quel est le coût en matière de performances de la prise d’un instantané ?

Lorsque le Débogueur de capture instantanée capture un instantané de votre application, il duplique (fork) le processu de l’application et interrompt la copie dupliquée. Lorsque vous déboguez un instantané, vous déboguez sur la copie dupliquée du processus. Ce processus ne prend que 10 à 20 millisecondes, mais ne copie pas le tas complet de l’application. À la place, il copie uniquement la table des pages et définit les pages sur « copie pour écriture ». Si certains des objets de votre application sur la pile changent, leurs pages correspondantes sont alors copiées. C’est pourquoi chaque capture instantanée a un petit coût en mémoire (de l’ordre de centaines de kilo-octets pour la plupart des applications).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Que se passe-t-il si j’ai un Azure App Service scaled-out (plusieurs instances de mon application) ?

Lorsque vous avez plusieurs instances de votre application, les snappoints sont appliqués à chaque instance unique. Seul le premier snappoint à atteindre les conditions spécifiées crée un instantané. Si vous avez plusieurs snappoints, les instantanés ultérieurs proviennent de l’instance qui a créé le premier instantané. Les logpoints envoyés à la fenêtre de sortie affichent uniquement les messages d’une instance, tandis que les logpoints envoyés aux journaux d’application envoient des messages à partir de chaque instance.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Comment le Débogueur de capture instantanée charge-t-il des symboles ?

Le Débogueur de capture instantanée nécessite que vous ayez les symboles correspondants pour votre application de manière locale ou déployée sur votre Azure App Service. (Les fichiers PDB incorporés ne sont actuellement pas pris en charge.) Le Débogueur de capture instantanée télécharge automatiquement les symboles à partir de votre Azure App Service. À partir de Visual Studio 2017 version 15.2, le déploiement sur Azure App Service déploie également les symboles de votre application.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Le Débogueur de capture instantanée fonctionne-t-il avec les builds de publication de mon application ?

Oui. Le Débogueur de capture instantanée est prévu pour fonctionner sur les builds de publication. Lorsqu’un snappoint est placé dans une fonction, la fonction est recompilée dans une version de débogage, pour la rendre compatible avec le débogage. L’arrêt du Débogueur de capture instantanée restaure les fonctions sur la build de publication.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Les logpoints peuvent-ils provoquer des effets secondaires dans mon application de production ?

Non. Les messages de journal que vous ajoutez à votre application sont évalués de manière virtuelle. Ils ne peuvent pas causer d’effets secondaires dans votre application. Toutefois, certaines propriétés natives peuvent ne pas être accessibles avec les logpoints.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Le Débogueur de capture instantanée fonctionne-t-il si mon serveur est en charge ?

Oui, le débogage d’instantané peut fonctionner pour les serveurs en charge. Le Débogueur de capture instantanée limite et ne capture pas les instantanés en cas de faible quantité de mémoire disponible sur votre serveur.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Comment désinstaller le Débogueur de capture instantanée ?

Vous pouvez désinstaller l’extension de site du Débogueur de capture instantanée sur votre App Service en procédant comme suit :

1. Désactivez votre App Service via le Cloud Explorer dans Visual Studio ou le Portail Azure.
1. Accédez au site Kudu de votre App Service (autrement dit, yourappservice.**scm**.azurewebsites.net) et accédez à **Extensions de site**.
1. Cliquez sur le X de l’extension de site du Débogueur de capture instantanée pour le supprimer.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Pourquoi les ports sont-ils ouverts pendant une session du Débogueur de capture instantanée ?

Le Débogueur de capture instantanée doit ouvrir un ensemble de ports pour déboguer les instantanés pris dans Azure, ce sont les mêmes ports requis pour le débogage distant. [Vous trouverez la liste des ports ici](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Comment faire désactiver l’extension du débogueur distant ?

Pour App Services :
1. Désactivez l’extension du débogueur distant via le Portail Azure pour votre App Service.
2. Portail Azure > le panneau des ressources du service d’application > paramètres de l' *application*
3. Accédez à la section *débogage* et cliquez sur le bouton *désactivé* pour le *débogage distant*.

Pour AKS :
1. Mettez à jour votre fichier dockerfile pour supprimer les sections correspondant à la [débogueur de capture instantanée Visual Studio sur les images de l’ancrage](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Régénérez et redéployez l’image de l’ancrage modifié.

Pour les machines virtuelles/groupes identiques de machines virtuelles, supprimez l’extension du débogueur distant, les certificats, les coffres de sauvegarde et les pools NAT entrants comme suit :

1. Supprimer l’extension du débogueur distant

   Il existe plusieurs façons de désactiver le débogueur distant pour les machines virtuelles et les groupes de machines virtuelles identiques :

      - Désactivez le débogueur distant via Cloud Explorer

         - Cloud Explorer > votre ressource de machine virtuelle > désactiver le débogage (la désactivation du débogage n’existe pas pour le groupe de machines virtuelles identiques sur Cloud Explorer).

      - Désactiver le débogueur distant avec les scripts/applets de commande PowerShell

         Pour la machine virtuelle :

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Pour les groupes de machines virtuelles identiques :

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Désactivez le débogueur distant via le Portail Azure
         - Portail Azure > le panneau de ressources de votre machine virtuelle/groupes de machines virtuelles identiques > extensions
         - Désinstallation de l’extension Microsoft. VisualStudio. Azure. RemoteDebug. VSRemoteDebugger

         > [!NOTE]
         > Groupes de machines virtuelles identiques : le portail n’autorise pas la suppression des ports DebuggerListener. Vous devrez utiliser Azure PowerShell. Voir les détails ci-dessous.

2. Supprimer des certificats et Azure Key Vault

   Lors de l’installation de l’extension du débogueur distant pour les machines virtuelles ou les groupes de machines virtuelles identiques, les certificats client et serveur sont créés pour authentifier le client Visual Studio avec les ressources de machine virtuelle Azure/groupes de machines virtuelles identiques.

   - Le certificat client

      Ce certificat est un certificat auto-signé situé dans CERT:/CurrentUser/My/

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Une façon de supprimer ce certificat de votre ordinateur est d’utiliser PowerShell

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - Certificat de serveur
      - L’empreinte de certificat de serveur correspondante est déployée en tant que secret dans Azure Key Vault. Visual Studio tente de trouver ou de créer un coffre de stockage avec préfixe MSVSAZ * dans la région correspondant à la ressource machine virtuelle ou groupes de machines virtuelles identiques. Toutes les ressources de machines virtuelles ou de groupes identiques de machines virtuelles déployées dans cette région partageront donc le même coffre de stockage.
      - Pour supprimer le secret de l’empreinte numérique du certificat de serveur, accédez au Portail Azure et recherchez le MSVSAZ * Key Vault dans la même région que celle qui héberge votre ressource. Supprimer la clé secrète qui doit être étiquetée `remotedebugcert<<ResourceName>>`
      - Vous devrez également supprimer le secret du serveur de votre ressource via PowerShell.

      Pour les machines virtuelles :

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Pour les groupes de machines virtuelles identiques :

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Supprimer tous les pools NAT entrants DebuggerListener (groupe de machines virtuelles identiques uniquement)

   Le débogueur distant introduit des pools NAT DebuggerListeners entrants qui sont appliqués à l’équilibreur de charge de votre identiques.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Comment faire désactiver Débogueur de capture instantanée ?

Pour App Service :
1. Désactivez Débogueur de capture instantanée par le biais du Portail Azure pour votre App Service.
2. Portail Azure > le panneau des ressources du service d’application > paramètres de l' *application*
3. Supprimez les paramètres d’application suivants dans le Portail Azure et enregistrez vos modifications.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Toute modification apportée aux paramètres de l’application lance un redémarrage de l’application. Pour plus d’informations sur les paramètres d’application, consultez [configurer une application App service dans le portail Azure](/azure/app-service/web-sites-configure).

Pour AKS :
1. Mettez à jour votre fichier dockerfile pour supprimer les sections correspondant à la [débogueur de capture instantanée Visual Studio sur les images de l’ancrage](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Régénérez et redéployez l’image de l’ancrage modifié.

Pour les machines virtuelles/groupes identiques de machines virtuelles :

Il existe plusieurs façons de désactiver les Débogueur de capture instantanée :
- Cloud Explorer > la ressource de votre machine virtuelle/groupe de machines virtuelles identiques > désactiver les Diagnostics

- Portail Azure > le panneau de ressources de votre machine virtuelle/groupe de machines virtuelles identiques > extensions > désinstaller Microsoft. Insights. Vmdiagnosticssettings lui extension

- Applets de commande PowerShell à partir de [AZ PowerShell](/powershell/azure/overview)

   Machine virtuelle :

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   Groupes identiques de machines virtuelles :

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.yml)
- [Déboguer des applications ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-applications.md)
- [Déboguer des groupes de machines virtuelles Azure Machines\Virtual ASP.NET en direct à l’aide du Débogueur de capture instantanée](../debugger/debug-live-azure-virtual-machines.md)
- [Déboguer Azure Kubernetes ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-kubernetes.md)
- [Résolution des problèmes et problèmes connus du débogage d’instantané](../debugger/debug-live-azure-apps-troubleshooting.md)
