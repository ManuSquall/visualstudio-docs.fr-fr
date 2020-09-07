---
title: Diagnostics pour Azure Cloud Services et les machines virtuelles Azure
description: Découvrez comment configurer les diagnostics pour le débogage des services cloud et des machines virtuelles Azure dans Visual Studio.
author: ghogen
manager: jillfra
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.openlocfilehash: 9912a7fa0e83c5433e0eba1c7ffa23763331af6b
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508494"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Configurer les diagnostics pour les services cloud et les machines virtuelles Azure
Quand vous devez résoudre les problèmes d’un service cloud ou d’une machine virtuelle Azure, vous pouvez utiliser Visual Studio pour configurer plus facilement les diagnostics Azure. Les diagnostics capturent les données système et les données de journalisation sur les machines virtuelles et sur les instances de machine virtuelle qui exécutent votre service cloud. Les données de diagnostic sont transférées à un compte de stockage que vous choisissez. Pour plus d’informations sur la journalisation des diagnostics dans Azure, consultez [Activer la journalisation des diagnostics pour les applications web dans Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

Dans cet article, nous vous montrons comment utiliser Visual Studio pour activer et configurer les diagnostics Azure avant et après le déploiement. Découvrez comment configurer les diagnostics sur des machines virtuelles Azure, comment sélectionner les types d’informations de diagnostic à collecter et comment les afficher une fois collectées.

Vous pouvez utiliser une des options suivantes pour configurer les diagnostics Azure :

* Changez les paramètres des diagnostics via la boîte de dialogue **Configuration des diagnostics** dans Visual Studio. Les paramètres sont enregistrés dans un fichier nommé diagnostics.wadcfgx (le fichier est nommé diagnostics.wadcfg dans Azure SDK 2.4 et antérieur). Vous pouvez aussi modifier directement le fichier de configuration. Si vous mettez le fichier à jour manuellement, les changements de configuration prennent effet lors du déploiement suivant du service cloud sur Azure, ou lors de son exécution dans l’émulateur.
* Pour modifier les paramètres des diagnostics pour un service cloud ou une machine virtuelle en cours d’exécution, utilisez Cloud Explorer ou l’Explorateur de serveurs dans Visual Studio.

## <a name="azure-sdk-26-diagnostics-changes"></a>Modifications apportées aux diagnostics d’Azure SDK 2.6
Les modifications suivantes s’appliquent aux projets Azure SDK 2.6 et ultérieur dans Visual Studio :

* L’émulateur local prend désormais en charge les diagnostics. Cela signifie que vous pouvez collecter les données de diagnostic et vérifier que votre application crée les traces appropriées quand vous développez et que vous testez dans Visual Studio. La chaîne `UseDevelopmentStorage=true` de connexion active la collecte des données de diagnostic pendant que vous exécutez votre projet de service Cloud dans Visual Studio à l’aide de l’émulateur de stockage Azure. Toutes les données de diagnostic sont collectées dans le compte de stockage Stockage de développement.
* La chaîne de connexion de compte de stockage des diagnostics `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` est stockée dans le fichier de configuration (.cscfg) du service. Dans Azure SDK 2.5, le compte de stockage des diagnostics est spécifié dans le fichier diagnostics.wadcfgx.

La chaîne de connexion présente certaines différences de fonctionnement importantes dans Azure SDK 2.6 et ultérieur par rapport à Azure SDK 2.4 et antérieur :

* Dans Azure SDK 2.4 et antérieur, la chaîne de connexion est utilisée comme runtime par le plug-in des diagnostics pour obtenir les informations du compte de stockage pour le transfert des journaux de diagnostics.
* Dans Azure SDK 2.6 et ultérieur, Visual Studio utilise la chaîne de connexion des diagnostics pour configurer l’extension de diagnostics Azure avec les informations du compte de stockage approprié lors de la publication. Vous pouvez utiliser la chaîne de connexion pour définir des comptes de stockage différents pour différentes configurations de service utilisées par Visual Studio lors de la publication. Cependant, comme le plug-in des diagnostics n’est plus disponible après Azure SDK 2.5, le fichier .cscfg ne peut pas activer lui-même l’extension des diagnostics. Vous devez configurer l’extension séparément avec des outils comme Visual Studio ou PowerShell.
* Pour simplifier le processus de configuration de l’extension des diagnostics avec PowerShell, la sortie du package provenant de Visual Studio contient également le code XML de la configuration publique pour l’extension des diagnostics pour chaque rôle. Visual Studio utilise la chaîne de connexion des diagnostics pour renseigner les informations du compte de stockage dans la configuration publique. Les fichiers de la configuration publique sont créés dans le dossier Extensions. Les fichiers de la configuration publique utilisent le modèle de nommage PaaSDiagnostics.&lt;nom_rôle\>.PubConfig.xml. Les déploiements basés sur PowerShell peuvent utiliser ce modèle pour mapper chaque configuration à un rôle.
* Le [portail Azure](https://portal.azure.com) utilise la chaîne de connexion du fichier .cscfg pour accéder aux données de diagnostic. Les données s’affichent sous l’onglet **analyse** . La chaîne de connexion est requise pour définir le service afin d’afficher les données de surveillance détaillées dans le portail.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Migrer des projets vers Azure SDK 2.6 et ultérieur
Quand vous migrez depuis Azure SDK 2.5 vers Azure SDK 2.6 ou ultérieur, si vous avez un compte de stockage des diagnostics spécifié dans le fichier .wadcfgx, ce compte reste dans ce fichier. Pour tirer parti de la souplesse que représente l’utilisation de comptes de stockage différents pour différentes configurations de stockage, ajoutez manuellement la chaîne de connexion à votre projet. Si vous migrez un projet depuis Azure SDK 2.4 ou antérieur vers Azure SDK 2.6, les chaînes de connexion de diagnostic sont conservées. Notez cependant les modifications apportées à la façon dont les chaînes de connexion sont traitées dans Azure SDK 2.6, qui est décrite dans la section précédente.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Détermination du compte de stockage des diagnostics par Visual Studio
* Si une chaîne de connexion des diagnostics est spécifiée dans le fichier .cscfg, Visual Studio l’utilise pour configurer l’extension des diagnostics lors de la publication et lors de la génération des fichiers XML de configuration publique durant l’empaquetage.
* Si une chaîne de connexion des diagnostics n’est pas spécifiée dans le fichier .cscfg, Visual Studio utilise alors le compte de stockage spécifié dans le fichier .wadcfgx pour configurer l’extension des diagnostics lors de la publication et de la génération des fichiers XML de configuration publique durant l’empaquetage.
* La chaîne de connexion des diagnostics dans le fichier .cscfg est prioritaire sur le compte de stockage dans le fichier .wadcfgx. Si une chaîne de connexion des diagnostics est spécifiée dans le fichier .cscfg, Visual Studio l’utilise et ignore le compte de stockage spécifié dans .wadcfgx.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>Que fait la case à cocher « Mettre à jour les chaînes de connexion du stockage de développement…» ?
La case à cocher **Mettre à jour les chaînes de connexion du stockage de développement pour les diagnostics et le Caching avec les informations d’identification du compte de stockage Microsoft Azure lors de la publication vers Microsoft Azure** offre un moyen pratique pour mettre à jour les chaînes de connexion de compte de stockage de développement avec le compte de stockage Azure spécifié lors de la publication.

Par exemple, si vous cochez cette case et que la chaîne de connexion des diagnostics spécifie `UseDevelopmentStorage=true`, quand vous publiez le projet sur Azure, Visual Studio met automatiquement à jour la chaîne de connexion des diagnostics avec le compte de stockage que vous avez spécifié dans l’Assistant Publication. Cependant, si un compte de stockage réel a été spécifié comme chaîne de connexion des diagnostics, ce compte est utilisé à la place.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Différences des fonctionnalités de diagnostic dans le kit de développement logiciel (SDK) Azure 2,4 et versions antérieures par rapport à Azure SDK 2,5 et versions ultérieures
Si vous mettez à niveau votre projet depuis Azure SDK 2.4 vers Azure SDK 2.5 ou ultérieur, vous devez garder à l’esprit les différences existant entre les fonctionnalités de diagnostics suivantes :

* **Les API de configuration sont dépréciées**. La configuration par programmation des diagnostics est disponible dans Azure SDK 2.4 et antérieur, mais elle est dépréciée dans Azure SDK 2.5 et ultérieur. Si votre configuration des diagnostics est actuellement définie dans du code, vous devez reconfigurer entièrement ces paramètres dans le projet migré pour que les diagnostics continuent de fonctionner. Le fichier de configuration des diagnostics pour Azure SDK 2.4 est diagnostics.wadcfg. Le fichier de configuration des diagnostics pour Azure SDK 2.5 est diagnostics.wadcfgx.
* **Les diagnostics pour les applications de service cloud peuvent être configurés seulement au niveau du rôle**. Dans Azure SDK 2.5 et ultérieur, vous ne pouvez pas configurer les diagnostics pour les applications de service cloud au niveau de l’instance.
* **Chaque fois que vous déployez votre application, la configuration des diagnostics est mise à jour**. Ceci peut occasionner des problèmes de parité si vous modifiez votre configuration des diagnostics à partir de l’Explorateur de serveurs de Visual Studio, puis que vous redéployez votre application.
* **Dans Azure SDK 2.5 et ultérieur, les vidages sur incident sont configurés dans le fichier de configuration des diagnostics et non pas dans le code**. Si vous avez des vidages sur incident configurés dans le code, vous devez transférer manuellement la configuration depuis le code vers le fichier de configuration. Les vidages sur incident ne sont pas transférés lors de la migration vers Azure SDK 2.6.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Activer les diagnostics dans les projets de service cloud avant leur déploiement
Dans Visual Studio, vous pouvez collecter les données de diagnostic pour des rôles qui s’exécutent dans Azure quand vous exécutez le service dans l’émulateur avant le déploiement. Toutes les modifications apportées aux paramètres de diagnostic dans Visual Studio sont enregistrées dans le fichier de configuration diagnostics.wadcfgx. Ces paramètres spécifient le compte de stockage où les données de diagnostic sont enregistrées quand vous déployez votre service cloud.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Pour activer les diagnostics dans Visual Studio avant le déploiement

1. Dans le menu contextuel pour le rôle, sélectionnez **Propriétés**. Dans la boîte de dialogue **Propriétés** du rôle, sélectionnez l’onglet **Configuration**.
2. Dans la section **Diagnostics**, vérifiez que la case à cocher **Activer les diagnostics** est activée.

    ![Accéder à l’option Activer les diagnostics](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Pour spécifier le compte de stockage pour les données de diagnostic, cliquez sur le bouton avec les points de suspension (...).

    ![Spécifier le compte de stockage à utiliser](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. Dans la boîte de dialogue **créer une chaîne de connexion de stockage** , spécifiez si vous souhaitez vous connecter à l’aide de l’émulateur de stockage Azure, d’un abonnement Azure ou d’informations d’identification entrées manuellement.

    ![Boîte de dialogue Compte de stockage](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)

   * Si vous sélectionnez **émulateur de stockage Microsoft Azure**, la chaîne de connexion est définie sur `UseDevelopmentStorage=true` .
   * Si vous choisissez **Votre abonnement**, vous pouvez choisir l’abonnement Azure que vous voulez utiliser et entrer un nom de compte. Pour gérer vos abonnements Azure, sélectionnez **Gérer les comptes**.
   * Si vous sélectionnez **Informations d’identification entrées manuellement**, entrez le nom et la clé du compte Azure que vous voulez utiliser.
5. Pour afficher la boîte de dialogue **Configuration des diagnostics**, sélectionnez **Configurer**. Excepté pour **Général** et **Répertoires de journaux**, chaque onglet représente une source de données de diagnostic que vous pouvez collecter. L’onglet par défaut **Général** offre les options de collecte de données de diagnostic suivantes : **Erreurs uniquement**, **Toutes les informations** et **Plan personnalisé**. L’option par défaut, **Erreurs uniquement**, utilise le plus petit volume de stockage, car elle ne transfère pas les messages d’avertissement ou de suivi. L’option **Toutes les informations** transfère le plus grand nombre d’informations, utilise le plus de stockage et est dès lors la plus coûteuse.

   > [!NOTE]
   > La taille minimale prise en charge pour « quota de disque en Mo » est de 50 Mo, et la taille par défaut est 4 Go. Toutefois, si vous collectez les vidages de mémoire, définissez ce paramètre sur une valeur supérieure, par exemple, 10 Go.
   >

    ![Activer les diagnostics Azure et la configuration](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. Pour cet exemple, sélectionnez l’option **Plan personnalisé** pour pouvoir personnaliser les données collectées.
7. Dans la zone **Quota de disque en Mo**, vous pouvez spécifier l’espace à allouer aux données de diagnostic dans votre compte de stockage. Vous pouvez changer ou accepter la valeur par défaut.
8. Sous chaque onglet des données de diagnostic que vous souhaitez collecter, activez la case à cocher **activer le transfert \<log type\> ** . Par exemple, si vous voulez collecter les journaux d’activité d’application, sous l’onglet **Journaux d’activité d’application**, cochez la case **Activer le transfert des journaux des applications**. Spécifiez également les autres informations nécessaires pour chaque type de données de diagnostic. Pour plus d’informations sur la configuration de chaque onglet, consultez la section **Configurer les sources de données de diagnostic** plus loin dans cet article.
9. Après avoir activé la collecte de toutes les données de diagnostic souhaitées, sélectionnez **OK**.
10. Exécutez votre projet de service cloud Azure dans Visual Studio comme d’habitude. À mesure que vous utilisez votre application, les informations de journalisation que vous avez sélectionnées sont enregistrées dans le compte de stockage Azure que vous avez spécifié.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Activer les diagnostics sur des machines virtuelles Azure
Dans Visual Studio, vous pouvez collecter des données de diagnostic pour des machines virtuelles Azure.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Pour activer les diagnostics sur des machines virtuelles Azure

1. Dans l’Explorateur de serveurs, sélectionnez le nœud Azure, puis connectez-vous à votre abonnement Azure si vous n’y êtes pas encore connecté.
2. Développez le nœud **Machines virtuelles**. Vous pouvez créer une machine virtuelle ou sélectionner un nœud existant.
3. Dans le menu contextuel de la machine virtuelle souhaitée, sélectionnez **Configurer**. La boîte de dialogue de configuration de la machine virtuelle apparaît.

    ![Configurer une machine virtuelle Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Ajoutez l’extension Microsoft Monitoring Agent Diagnostics si elle n’est pas déjà installée. Avec cette extension, vous pouvez collecter des données de diagnostic pour la machine virtuelle Azure. Sous **Extensions installées**, dans la liste déroulante **Sélectionner une extension disponible**, sélectionnez **Microsoft Monitoring Agent Diagnostics**.

    ![Installer une extension de machine virtuelle Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)

    > [!NOTE]
   > D’autres extensions des diagnostics sont disponibles pour vos machines virtuelles. Pour plus d’informations, consultez [Extensions et fonctionnalités de machine virtuelle pour Windows](/azure/virtual-machines/windows/extensions-features).
   >
   >
5. Pour ajouter l’extension et afficher sa boîte de dialogue **Configuration des diagnostics**, sélectionnez **Ajouter**.
6. Pour spécifier un compte de stockage, sélectionnez **Configurer**, puis sélectionnez **OK**.

    Chaque onglet (à l’exception de **Général** et **Répertoires de journaux**) représente une source de données de diagnostic que vous pouvez collecter.

    ![Activer les diagnostics Azure et la configuration](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)

    L’onglet par défaut, **Général**, offre les options de collecte de données de diagnostic suivantes : **Erreurs uniquement**, **Toutes les informations** et **Plan personnalisé**. L'option par défaut, **Erreurs uniquement**, nécessite le plus petit volume de stockage, car elle ne transfère pas les messages d'avertissement ou de suivi. L'option **Toutes les informations** transfère le plus grand nombre d'informations. Elle est donc la plus coûteuse en termes de stockage.
7. Pour cet exemple, sélectionnez l'option **Plan personnalisé** afin de pouvoir sélectionner les données collectées.
8. Le champ **Quota de disque en Mo** spécifie l'espace à allouer aux données de diagnostic dans le compte de stockage. Vous pouvez modifier la valeur par défaut si vous le souhaitez.
9. Sous chaque onglet des données de diagnostic à collecter, activez la case à cocher **Activer le transfert de \<log type\>**.

    Par exemple, si vous souhaitez collecter les journaux d’application, activez la case à cocher **activer le transfert des journaux des applications** sous l’onglet **journaux des applications** . Spécifiez également les autres informations requises pour chaque type de données de diagnostic. Pour plus d’informations sur la configuration de chaque onglet, consultez la section **Configurer les sources de données de diagnostic** plus loin dans cet article.
10. Après avoir activé la collecte de toutes les données de diagnostic souhaitées, sélectionnez **OK**.
11. Enregistrez le projet mis à jour.

    Un message s’affiche dans la fenêtre **Journal des activités Microsoft Azure**, indiquant que la machine virtuelle a été mise à jour.

## <a name="set-up-diagnostics-data-sources"></a>Configurer des sources de données de diagnostic
Après avoir activé la collecte des données de diagnostic, vous pouvez sélectionner les sources de données et les informations à collecter. Les sections suivantes décrivent les onglets de la boîte de dialogue **Configuration des diagnostics** et la signification de chaque option de configuration.

### <a name="application-logs"></a>Journaux d’activité d’application
Les journaux d’activité d’application contiennent des informations de diagnostic produites par une application web. Si vous voulez capturer les journaux d'application, sélectionnez la case à cocher **Activer le transfert des journaux d'application**. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux d’activité d’application vers votre compte de stockage, vous devez changer la valeur de **Période de transfert (min)**. Vous pouvez également changer la quantité d’informations consignées dans le journal en définissant la valeur de **Niveau de journalisation**. Par exemple, sélectionnez **Détaillé** pour collecter plus d’informations ou **Critique** pour capturer seulement les erreurs critiques. Si vous avez un fournisseur de diagnostics spécifique qui génère des journaux d’activité d’application, vous pouvez capturer ceux-ci en ajoutant le GUID du fournisseur dans la zone **GUID du fournisseur**.

  ![Journaux d’activité d’application](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Pour plus d’informations sur les journaux d’activité d’application, consultez [Activer la journalisation des diagnostics pour les applications web dans Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Journaux d’événements Windows
Pour capturer les journaux des événements Windows, cochez la case **Activer le transfert des journaux des événements Windows**. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux des événements vers votre compte de stockage, changez la valeur de **Période de transfert (min)**. Activez les cases à cocher correspondant aux types d’événements que vous voulez suivre.

![Journaux d’événements](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Si vous utilisez le kit de développement logiciel (SDK) Azure 2,6 ou une version ultérieure et que vous souhaitez spécifier une source de données personnalisée, entrez-la dans la **\<Data source name\>** zone de texte, puis sélectionnez **Ajouter**. La source de données est ajoutée au fichier diagnostics.cfcfg.

Si vous utilisez Azure SDK 2.5 et que vous voulez spécifier une source de données personnalisée, vous pouvez l’ajouter à la section `WindowsEventLog` du fichier diagnostics.wadcfgx, comme dans l’exemple suivant :

```xml
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```

### <a name="performance-counters"></a>Compteurs de performance
Les informations d’un compteur de performances peuvent vous aider à localiser des goulets d’étranglement système et à affiner les performances des applications et du système. Pour plus d’informations, consultez [Créer et utiliser des compteurs de performances dans une application Azure](/azure/cloud-services/diagnostics-performance-counters) . Pour capturer des compteurs de performances, cochez la case **Activer le transfert des compteurs de performances**. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux des événements vers votre compte de stockage, changez la valeur de **Période de transfert (min)**. Activez les cases à cocher correspondant aux compteurs de performances que vous voulez suivre.

![Compteurs de performance](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Pour suivre un compteur de performances qui n’est pas répertorié, entrez-le en utilisant la syntaxe suggérée. Sélectionnez ensuite **Ajouter**. Le système d’exploitation de la machine virtuelle détermine les compteurs de performances que vous pouvez suivre. Pour plus d’informations sur la syntaxe, consultez [spécifier un chemin d’accès de compteur](/windows/win32/perfctrs/specifying-a-counter-path).

### <a name="infrastructure-logs"></a>Journaux d’activité d’infrastructure
Les journaux d’activité d’infrastructure contiennent des informations sur l’infrastructure de diagnostic Azure, le module RemoteAccess et le module RemoteForwarder. Pour collecter des informations sur les journaux d’activité d’infrastructure, cochez la case **Activer le transfert des journaux d’activité d’infrastructure**. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux d’activité d’infrastructure vers votre compte de stockage, changez la valeur de **Période de transfert (min)**.

![Journaux d’activité d’infrastructure de diagnostics](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Pour plus d’informations, consultez [Collecter des données de journalisation avec les diagnostics Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="log-directories"></a>Répertoires de journaux
Les répertoires de journaux contiennent des données collectées à partir de répertoires de journaux pour les demandes, les demandes ayant échoué ou les dossiers IIS que vous choisissez. Pour capturer les répertoires de journaux, cochez la case **Activer le transfert des répertoires de journaux**. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux d’activité vers votre compte de stockage, changez la valeur de **Période de transfert (min)**.

Cochez les cases correspondant aux journaux d’activité à collecter, comme **Journaux d’activité IIS** et **Journaux d’activité de demandes ayant échoué**. Des noms de conteneurs de stockage par défaut sont fournis, mais vous pouvez les changer.

Vous pouvez capturer des journaux d’activité de n’importe quel dossier. Spécifiez le chemin dans la section **Journal du répertoire absolu**, puis sélectionnez **Ajouter le répertoire**. Les journaux d’activité sont capturés dans les conteneurs spécifiés.

![Répertoires de journaux](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>Journaux d’activité de suivi des événements ETW
Si vous utilisez la fonction [Suivi d’événements pour Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) et souhaitez capturer les journaux d’activité ETW, sélectionnez la case à cocher **Activer le transfert des journaux d’activité ETW**. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux d’activité vers votre compte de stockage, changez la valeur de **Période de transfert (min)**.

Les événements sont capturés à partir de sources d’événements et de fichiers manifestes d’événements que vous spécifiez. Pour spécifier une source d’événements, dans la section **Sources d’événements**, entrez un nom, puis sélectionnez **Ajouter une source d’événements**. De même, vous pouvez spécifier un manifeste d’événements dans la section **Manifestes d’événements**, puis sélectionner **Ajouter un manifeste d’événements**.

![Journaux d’activité de suivi des événements ETW](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

L’infrastructure ETW est prise en charge dans ASP.NET via des classes de l’espace de noms [System.Diagnostics.aspx](/dotnet/api/system.diagnostics). L’espace de noms Microsoft.WindowsAzure.Diagnostics, qui hérite des classes [System.Diagnostics.aspx](/dotnet/api/system.diagnostics), permet d’utiliser [System.Diagnostics.aspx](/dotnet/api/system.diagnostics) comme infrastructure de journalisation dans l’environnement Azure. Pour plus d’informations, consultez [Contrôler la journalisation et le suivi dans Microsoft Azure](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) et [Activer les diagnostics dans les services cloud et les machines virtuelles Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Vidages sur incident
Pour capturer des informations sur le moment où une instance de rôle se bloque, cochez la case **Activer le transfert de vidages sur incident**. (Étant donné que ASP.NET gère la plupart des exceptions, cela n’est généralement utile que pour les rôles de travail.) Pour augmenter ou diminuer le pourcentage d’espace de stockage dédié aux vidages sur incident, modifiez la valeur **quota de répertoire (%)** . Vous pouvez changer le conteneur de stockage où les vidages sur incident sont stockés et choisir de capturer un vidage **Complet** ou **Mini**.

Les processus actuellement suivis sont répertoriés dans la capture d’écran suivante. Activez les cases à cocher correspondant aux processus que vous voulez capturer. Pour ajouter un processus à la liste, entrez le nom du processus, puis sélectionnez **Ajouter un processus**.

![Vidages sur incident](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Pour plus d’informations, consultez [Contrôler la journalisation et le suivi dans Microsoft Azure](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) et [Microsoft Azure Diagnostics Part 4: Custom Logging Components and Azure Diagnostics 1.3 Changes](https://www.red-gate.com/simple-talk/cloud/platform-as-a-service/microsoft-azure-diagnostics-part-4-custom-logging-components-and-azure-diagnostics-1.3-changes/).

## <a name="view-the-diagnostics-data"></a>Affichage des données de diagnostic
Après avoir collecté les données de diagnostic pour un service cloud ou une machine virtuelle, vous pouvez les visualiser.

### <a name="to-view-cloud-service-diagnostics-data"></a>Pour afficher les données de diagnostic d’un service cloud
1. Déployez votre service cloud comme d’habitude, puis exécutez-le.
2. Vous pouvez visualiser les données de diagnostic dans un rapport généré par Visual Studio ou dans des tables de votre compte de stockage. Pour afficher les données d’un rapport, ouvrez Cloud Explorer ou l’Explorateur de serveurs, ouvrez le menu contextuel du nœud pour le rôle de votre choix, puis sélectionnez **Afficher les données de diagnostic**.

    ![Afficher les données de diagnostic](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)

    Un rapport contenant les données disponibles s’affiche.

    ![Rapport Diagnostics Microsoft Azure dans Visual Studio](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)

    Si les données les plus récentes n’apparaissent pas, vous devez peut-être attendre la fin de la période de transfert.

    Pour mettre à jour les données immédiatement, sélectionnez le lien **Actualiser**. Pour que les données soient mises à jour automatiquement, sélectionnez un intervalle dans la liste déroulante **Actualiser automatiquement**. Pour exporter les données d’erreur, sélectionnez **Exporter au format CSV** pour créer un fichier de valeurs séparées par des virgules, que vous pouvez ouvrir dans une feuille de calcul Excel.

    Dans Cloud Explorer ou l’Explorateur de serveurs, ouvrez le compte de stockage associé au déploiement.
3. Ouvrez les tables de diagnostics dans la visionneuse de tables, puis étudiez les données que vous avez collectées. Pour les journaux d’activité IIS et les journaux d’activité personnalisés, vous pouvez ouvrir un conteneur d’objets blob. Le tableau suivant répertorie les tables ou les conteneurs d’objets blob qui contient les données pour les différents fichiers journaux. En plus des données pour ce fichier journal, les entrées de la table contiennent **EventTickCount**, **DeploymentId**, **Role** et **RoleInstance**, qui vous aident à identifier la machine virtuelle et le rôle qui ont généré les données et à quel moment.

   | Données de diagnostic | Description | Emplacement |
   | --- | --- | --- |
   | Journaux d’activité d’application |Journaux d’activité générés par votre code en appelant des méthodes de la classe **System.Diagnostics.Trace**. |WADLogsTable |
   | Journaux d’événements |Données des journaux d’événements Windows sur les machines virtuelles. Windows stocke des informations dans ces journaux d’activité, mais les applications et les services les utilisent également pour signaler des erreurs ou enregistrer des informations. |WADWindowsEventLogsTable |
   | Compteurs de performance |Vous pouvez collecter des données sur n’importe quel compteur de performance disponible sur la machine virtuelle. Le système d’exploitation fournit des compteurs de performances qui comprennent de nombreuses statistiques, comme l’utilisation de la mémoire et le temps processeur. |WADPerformanceCountersTable |
   | Journaux d’activité d’infrastructure |Journaux d’activité générés à partir de l’infrastructure de diagnostics elle-même. |WADDiagnosticInfrastructureLogsTable |
   | Journaux d’activité IIS |Journaux d’activité qui enregistrent les requêtes web. Si votre service cloud reçoit une quantité importante de trafic, ces journaux d’activité peuvent être longs. Il est judicieux de collecter et de stocker ces données seulement si vous en avez besoin. |Vous pouvez trouver les journaux d’activité des requêtes ayant échoué dans le conteneur d’objets blob sous wad-iis-failedreqlogs, dans un chemin pour ce déploiement, ce rôle et cette instance. Vous trouverez les journaux d’activité complets sous wad-iis-logfiles. Les entrées pour chaque fichier se font dans la table WADDirectories. |
   | Vidages sur incident |Fournit des images binaires du processus de votre service cloud (généralement un rôle Worker). |Conteneur d’objets blob wad-crush-dumps |
   | Fichiers journaux personnalisés |Journaux d’activité de données que vous avez prédéfinis. |Spécifiez dans le code l’emplacement des fichiers journaux personnalisés dans votre compte de stockage. Par exemple, vous pouvez spécifier un conteneur d’objets blob personnalisé. |
4. Si des données d’un type quelconque sont tronquées, vous pouvez tenter d’augmenter la mémoire tampon pour ce type de données ou de raccourcir l’intervalle entre les transferts de données de la machine virtuelle à votre compte de stockage.
5. (Facultatif) Videz de temps en temps les données du compte de stockage de façon à réduire les coûts de stockage généraux.
6. Lorsque vous effectuez un déploiement complet, le fichier diagnostics.cscfg (.wadcfgx pour le Kit de développement logiciel (SDK) Azure 2.5) est mis à jour dans Azure et votre service cloud sélectionne toutes les modifications apportées à votre configuration de diagnostics. Si au lieu de cela vous mettez à jour un déploiement existant, le fichier .cscfg n’est pas mis à jour dans Azure. Vous pouvez tout de même modifier les paramètres de diagnostics en suivant les étapes décrites dans la section qui suit. Pour plus d’informations sur l’exécution d’un déploiement complet et la mise à jour d’un déploiement existant, consultez [Assistant Publication d’application Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>Pour afficher les données de diagnostic d’une machine virtuelle
1. Dans le menu contextuel pour la machine virtuelle, sélectionnez **Afficher les données de diagnostic**.

    ![Afficher les données de diagnostic dans une machine virtuelle Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)

    La boîte de dialogue **Résumé des diagnostics** s’affiche.

    ![Résumé des diagnostics de la machine virtuelle Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)

    Si les données les plus récentes n’apparaissent pas, vous devez peut-être attendre la fin de la période de transfert.

    Pour mettre à jour les données immédiatement, sélectionnez le lien **Actualiser**. Pour que les données soient mises à jour automatiquement, sélectionnez un intervalle dans la liste déroulante **Actualiser automatiquement**. Pour exporter les données d’erreur, sélectionnez **Exporter au format CSV** pour créer un fichier de valeurs séparées par des virgules, que vous pouvez ouvrir dans une feuille de calcul Excel.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Configurer des diagnostics de service cloud après déploiement
Si vous recherchez des informations sur un problème dans un service cloud en cours d’exécution, vous pouvez collecter des données que vous n’aviez pas spécifiées avant le déploiement initial du rôle. Dans ce cas, vous pouvez commencer à collecter ces données en changeant les paramètres de l’Explorateur de serveurs. Vous pouvez configurer des diagnostics pour une seule instance ou pour toutes les instances d’un rôle, selon que vous ouvrez la boîte de dialogue **Configuration des diagnostics** depuis le menu contextuel de l’instance ou du rôle. Si vous configurez le nœud du rôle, les changements s’appliquent à toutes les instances. Si vous configurez le nœud de l’instance, les changements s’appliquent seulement à cette instance.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Pour configurer les diagnostics pour un service cloud en cours d’exécution
1. Dans l’Explorateur de serveurs, développez le nœud **Services cloud**, puis développez la liste des nœuds pour trouver le rôle ou l’instance (ou les deux) que vous voulez examiner.

    ![Configuration de la collecte des diagnostics](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. Dans le menu contextuel d’un nœud d’instance ou d’un nœud de rôle, sélectionnez **Mettre à jour les paramètres de diagnostics**, puis sélectionnez les paramètres des diagnostics que vous voulez collecter.

    Pour plus d’informations sur les paramètres de configuration, consultez la section **Configurer des sources de données de diagnostic** dans cet article. Pour plus d’informations sur la façon de visualiser les données de diagnostic, consultez **Afficher les données de diagnostic** dans cet article.

    Si vous modifiez la collecte de données dans l’Explorateur de serveurs, les modifications continuent à s’appliquer jusqu’au redéploiement complet de votre service cloud. Si vous utilisez les paramètres de publication par défaut, les modifications ne sont pas remplacées. Le paramètre de publication par défaut provoque la mise à jour du déploiement existant, et non pas un redéploiement complet. Pour garantir l’effacement des paramètres au moment du déploiement, accédez à l’onglet **Paramètres avancés** dans l’Assistant Publication, puis décochez la case **Mise à jour du déploiement**. Quand vous redéployez après avoir désactivé cette case à cocher, les paramètres sont rétablis avec les valeurs du fichier .wadcfgx (ou .wadcfg) tels que définis dans l’éditeur de **Propriétés** pour le rôle. Si vous mettez à jour votre déploiement, Azure conserve les paramètres précédents.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Dépannage de problèmes de service cloud Azure
Si vous rencontrez des problèmes avec vos projets de service cloud, par exemple si un rôle reste bloqué à l’état « occupé », s’il exécute un cycle en boucle ou s’il lève une erreur interne du serveur, il existe des outils et des techniques permettant de diagnostiquer et de corriger le problème. Pour des exemples spécifiques de problèmes courants et de solutions, et pour une vue d’ensemble des concepts et des outils que vous pouvez utiliser pour diagnostiquer et corriger ces erreurs, consultez [Azure PaaS compute diagnostics data](/archive/blogs/kwill/windows-azure-paas-compute-diagnostics-data).

## <a name="q--a"></a>Questions et réponses
**Qu’est-ce que la taille de la mémoire tampon et quelle doit-elle être ?**

Sur chaque instance de machine virtuelle, des quotas limitent la quantité de données de diagnostic qui peuvent être stockées sur le système de fichiers local. De plus, vous pouvez spécifier une taille de mémoire tampon pour chaque type de données de diagnostic disponible. Cette taille de mémoire tampon joue le rôle de quota individuel pour ce type de données. Pour déterminer le quota global et la quantité de mémoire restante, regardez dans la partie inférieure de la boîte de dialogue pour les types de données de diagnostic. En spécifiant des mémoires tampons plus grandes ou des types de données plus nombreux, vous vous approchez du quota général. Vous pouvez changer le quota global en modifiant le fichier de configuration diagnostics.wadcfg ou .wadcfgx. Les données de diagnostic sont stockées sur le même système de fichiers que les données de votre application. Si votre application utilise une grande quantité d’espace disque, n’augmentez pas le quota de diagnostic global.

**Qu’est-ce que la période de transfert et quelle doit être sa durée ?**

La période de transfert est le temps écoulé entre les captures de données. Après chaque période de transfert, les données sont déplacées du système de fichiers local d’une machine virtuelle aux tables de votre compte de stockage. Si la quantité de données collectées dépasse le quota avant la fin d’une période de transfert, les données plus anciennes sont écartées. Si vous perdez des données en raison du fait qu’elles dépassent la taille de la mémoire tampon ou le quota global, vous pouvez diminuer la période de transfert.

**Dans quel fuseau horaire se trouvent les horodatages ?**

Les horodatages correspondent au fuseau horaire local du centre de données qui héberge votre service cloud. Les trois colonnes d’horodatage suivantes sont utilisées dans les tables de journaux :

* **PreciseTimeStamp** : horodatage ETW de l’événement. Autrement dit, l’heure de l’événement est enregistrée à partir du client.
* **TIMESTAMP** : valeur de **PreciseTimeStamp** arrondie vers le bas à la limite de la fréquence de chargement. Par exemple, si votre fréquence de chargement est de 5 minutes et si l’heure de l’événement est 00:17:12, TIMESTAMP vaut 00:15:00.
* **Timestamp** : horodatage de la création de l’entité dans la table Azure.

**Comment gérer les coûts pendant la collecte d’informations de diagnostics ?**

Les paramètres par défaut (**Niveau du journal** défini sur **Erreur** et **Période de transfert** sur **1 minute**) sont conçus pour minimiser les coûts. Vos coûts de calcul augmentent dès lors que vous collectez plus de données de diagnostic ou que vous diminuez la période de transfert. Ne collectez pas plus de données que nécessaire et n’oubliez pas de désactiver la collecte de données quand vous n’en avez plus besoin. Vous pouvez toujours la réactiver, même au moment de l’exécution, comme décrit précédemment dans cet article.

**Comment recueillir des journaux d’activité de demandes IIS ayant échoué ?**

Par défaut, IIS ne collecte pas les journaux d’activité de demandes ayant échoué. Vous pouvez configurer IIS de façon à collecter des journaux d’activité pour les demandes ayant échoué en modifiant le fichier web.config pour votre rôle web.

**Je n’obtiens pas les informations des méthodes RoleEntryPoint comme OnStart. Que se passe-t-il ?**

Les méthodes de **RoleEntryPoint** sont appelées dans le contexte de WAIISHost.exe, et non dans IIS. Les informations de configuration dans web.config qui autorisent normalement le traçage ne s’appliquent pas. Pour résoudre ce problème, ajoutez un fichier. config à votre projet de rôle Web et nommez le fichier pour qu’il corresponde à l’assembly de sortie qui contient le code **RoleEntryPoint** . Dans le projet de rôle Web par défaut, le nom du fichier. config doit être WAIISHost.exe.config. Ajoutez les lignes suivantes à ce fichier :

```xml
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

Dans la fenêtre **Propriétés**, définissez la propriété **Copier dans le répertoire de sortie** sur **Toujours copier**.

## <a name="next-steps"></a>Étapes suivantes
Pour en savoir plus sur la journalisation des diagnostics dans Azure, consultez [Activer les diagnostics dans les services cloud et les machines virtuelles Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics) et [Activer la journalisation des diagnostics pour les applications web dans Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).
