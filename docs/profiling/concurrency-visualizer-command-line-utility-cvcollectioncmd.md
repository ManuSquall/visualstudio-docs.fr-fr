---
title: Utilitaire en ligne de commande du visualiseur concurrentiel (CVCollectionCmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a24bea13687d58d4d9b9d9dc8ecf0bec86595759
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951235"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Utilitaire en ligne de commande du visualiseur concurrentiel (CVCollectionCmd)
Vous pouvez utiliser l’utilitaire en ligne de commande du visualiseur concurrentiel (*CVCollectionCmd.exe*) pour collecter des traces à partir de la ligne de commande et les afficher dans le visualiseur concurrentiel pour Visual Studio. Vous pouvez utiliser ces outils sur des ordinateurs sur lesquels Visual Studio n'est pas installé.  

> [!NOTE]
>  À compter de Visual Studio 2013, le Visualiseur concurrentiel est une extension facultative (il était autrefois inclus dans Visual Studio). Vous pouvez télécharger les [Outils de collecte du visualiseur concurrentiel pour Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103) à partir du Centre de téléchargement.  

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Télécharger l’utilitaire en ligne de commande du visualiseur concurrentiel  
 Pour télécharger et installer l’utilitaire en ligne de commande, accédez aux [outils de collecte du visualiseur concurrentiel pour Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103) , puis suivez les instructions. Par défaut, *CVCollectionCmd.exe* est installé dans %ProgramFiles%\Microsoft Concurrency Visualizer Collection Tools\ (%ProgramFiles(x86)%\Microsoft Concurrency Visualizer Collection Tools\ sur les ordinateurs x64).  

## <a name="collect-a-trace-with-cvcollectioncmd"></a>Recueillir une trace avec CVCollectionCmd  
 Vous pouvez recueillir une trace en démarrant l’application avec CVCollectionCmd ou en vous y attachant. Pour plus d’informations sur les options, consultez ci-dessous les informations de référence sur les commandes. Exemple :  

```cmd  
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data  
```  

## <a name="commands-and-parameters"></a>Commandes et paramètres  
 Pour obtenir de l’aide sur les commandes et paramètres dans l’utilitaire en ligne de commande, tapez ce qui suit à l’invite de commandes :  

 **CvCollectionCmd /?**  

|Option|Description|Paramètres|Valeurs de retour|  
|------------|-----------------|----------------|-------------------|  
|Query|Retourne une valeur qui indique si la collecte peut démarrer.|Aucun.|0 si la collecte peut démarrer.<br /><br /> 1 si la collecte est déjà en cours.<br /><br /> 2 si la collecte n’est pas en cours, mais qu’une ou plusieurs des sessions [ETW](/dotnet/framework/wcf/samples/etw-tracing) nécessaires sont déjà activées.|  
|Lancer|Exécute le processus spécifié sous le Visualiseur concurrentiel.|Chemin de l’exécutable.|0 si l’exécution a réussi.<br /><br /> 1 si l’exécution a échoué en raison de l’impossibilité de démarrer l’application cible.<br /><br /> 13 si l’exécution a échoué en raison des autorisations de CVCollectionCmd, insuffisantes pour écrire dans le répertoire de sortie spécifié.|  
|Attach|Commence la collecte d’une trace à l’échelle du système ; sinon, établit une liaison avec un processus si vous en avez spécifié un.|Aucun.|0 si l’attachement a abouti.<br /><br /> 1 si l’attachement a échoué en raison de la non validité et du caractère ambigu du processus spécifié.<br /><br /> 13 si l’attachement a échoué en raison des autorisations de CVCollectionCmd, insuffisantes pour écrire dans le répertoire de sortie spécifié.|  
|Detach|Arrête la collecte.|Aucun.|0 si le détachement a réussi.<br /><br /> 1 si le détachement a échoué, car la collecte n’est pas en cours.<br /><br /> 2 si le détachement a échoué pour cause d’impossibilité d’arrêter la collecte.|  
|Analyze|Analyse la trace spécifiée.|Chemin du fichier CVTrace.|0 si l’analyse a abouti.<br /><br /> 1 si l’analyse n’a pas pu démarrer, car la trace spécifiée était à l’échelle du système, mais aucun processus cible n’a été spécifié.<br /><br /> 2 si l’analyse n’a pas pu démarrer, car la trace n’était pas à l’échelle du système et un processus a été spécifié.<br /><br /> 3 si l’analyse a échoué en raison de la non validité du processus spécifié.<br /><br /> 4 si l’analyse a échoué en raison de la non validité du fichier CVTrace spécifié.|  
|LaunchArgs|Spécifie les arguments exécutables cibles. Cette option s’applique uniquement à la commande Launch.|Arguments en ligne de commande de l’application.|Aucune.|  
|Outdir|Spécifie le répertoire dans lequel enregistrer les fichiers de trace. S’applique aux commandes Launch et Attach.|Chemin d’un répertoire ou chemin relatif.|Aucun.|  
|Process|Spécifie le processus auquel s’attacher en cas d’exécution de la commande Attach ou le processus d’une trace à analyser en cas d’exécution de la commande Analyze. S’applique aux commandes Attach et Analyze.|PID ou nom du processus.|Aucun.|  
|Config|Spécifie le chemin du fichier de configuration, si vous souhaitez appliquer des paramètres de collecte autres que les paramètres par défaut.   S’applique aux commandes Launch, Attach et Analyze.|Chemin du répertoire ou chemin relatif du fichier de configuration XML.|Aucun.|  

## <a name="customize-configuration-settings"></a>Personnaliser les paramètres de configuration  
 Si vous utilisez CVCollectionCmd pour recueillir des traces et que vous voulez personnaliser les paramètres de collecte, utilisez un fichier de configuration pour les spécifier.  

> [!NOTE]
>  Quand vous utilisez Visual Studio pour recueillir des traces, ne modifiez pas directement le fichier de configuration.  Au lieu de cela, utilisez la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) pour modifier les paramètres.  

 Pour modifier les paramètres de collecte, créez un fichier de configuration sur l’ordinateur où vous exécuterez l’utilitaire CVCollectionCmd. Vous pouvez créer ce fichier de configuration de toutes pièces ou copier celui qui se trouve sur l’ordinateur où Visual Studio est installé et le modifier. Le fichier se nomme *UserConfig.xml* et se trouve dans le dossier *AppData Local*. Quand vous exécutez l’utilitaire, utilisez l’option Config avec la commande Launch, Attach ou Analyze.  Dans le paramètre associé à l’option Config, spécifiez le chemin du fichier de configuration.  

### <a name="configuration-file-tags"></a>Balises du fichier config  
 Le fichier de configuration est basé sur la norme XML. Voici les balises et les valeurs valides :  


| Balise | Description | Valeurs |
|-------------------------| - | - |
| Config | Délimite le fichier de configuration dans son ensemble. | Doit contenir les éléments suivants :<br /><br /> -   MinorVersion<br />-   MajorVersion |
| MajorVersion | Spécifie la version majeure du fichier de configuration. | Doit avoir la valeur 1 pour les projets [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] . Si la valeur est différente de 1, l’utilitaire ne fonctionne pas. |
| MinorVersion | Spécifie la version mineure du fichier de configuration. | Doit avoir la valeur 0 pour les projets [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] . Si la valeur est différente de 0, l’utilitaire ne fonctionne pas. |
| IncludeEnvSymbolPath | Définit une valeur qui détermine si le chemin du symbole d’environnement (_NT_SYMBOL_PATH) est utilisé. | -   True<br />-   False |
| DeleteEtlsAfterAnalysis | Définit une valeur qui détermine si les fichiers ETL sont supprimés une fois l’analyse terminée. | -   True<br />-   False |
| SymbolPath | Spécifie le chemin du serveur de symboles. Pour plus d’informations, consultez [Utiliser le serveur de symboles Microsoft pour obtenir des fichiers de symboles de débogage](http://go.microsoft.com/fwlink/?LinkID=149389). | Nom de répertoire ou URL. |
| Markers | Contient la liste des fournisseurs de marqueurs. | Peut contenir zéro, un ou plusieurs éléments MarkerProvider. |
| MarkerProvider | Spécifie un fournisseur de marqueurs unique. | Doit contenir les éléments suivants :<br /><br /> -   Level<br />-   GUID<br />-   Name<br /><br /> Peut contenir les éléments suivants :<br /><br /> -   Categories<br />-   IsEnabled |
| Niveau | Définit le niveau d’importance d’un MarkerProvider. | -   Low<br />-   Normal<br />-   High<br />-   Critical<br />-   Everything |
| GUID | Identificateur global unique du fournisseur de marqueurs ETW. | GUID. |
| Name | Spécifie la description du fournisseur de marqueurs. | Chaîne. |
| Categories | Spécifie les catégories recueillies pour le fournisseur de marqueurs. | Chaîne de nombres ou de plages de nombres délimitée par des virgules. |
| IsEnabled | Définit une valeur qui détermine si le fournisseur de marqueurs est activé pour la collecte. | -   True<br />-   False |
| FilterConfig | Spécifie la liste d’options de configuration des événements ETW filtrés à partir de la collecte. | Peut contenir les éléments suivants :<br /><br /> -   CollectClrEvents<br />-   ClrCollectionOptions<br />-   CollectSampleEvents<br />-   CollectGpuEvents<br />-   CollectFileIO |
| CollectClrEvents | Définit une valeur qui détermine si les événements CLR sont recueillis. | -   True<br />-   False |
| ClrCollectionOptions | Spécifie s’il faut recueillir les événements CLR pour les applications natives et s’il faut recueillir les événements d’arrêt NGEN. | Peut contenir une de ces valeurs, les deux ou aucune :<br /><br /> -   CollectForNative<br />-   DisableNGenRundown |
| CollectSampleEvents | Définit une valeur qui détermine si des exemples d’événements sont recueillis. | -   True<br />-   False |
| CollectGpuEvents | Définit une valeur qui détermine si les événements générés par DX sont recueillis. | -   True<br />-   False |
| CollectFileIO | Définit une valeur qui détermine si les événements d’E/S de fichier sont recueillis. | -   True<br />-   False |
| UserBufferSettings | Spécifie la liste de paramètres de mémoire tampon utilisateur. | Doit contenir les éléments suivants :<br /><br /> -   BufferFlushTimer<br />-   BufferSize<br />-   MinimumBuffers<br />-   MaximumBuffers |
| KernelBufferSettings | Spécifie la liste des paramètres de mémoire tampon du noyau. | Doit contenir les éléments suivants :<br /><br /> -   BufferFlushTimer<br />-   BufferSize<br />-   MinimumBuffers<br />-   MaximumBuffers |
| BufferFlushTimer | Spécifie l’horloge de vidage des mémoires tampons ETW. | Entier positif. |
| BufferSize | Quantité de mémoire allouée à chaque mémoire tampon de session de suivi des événements, en kilo-octets. | Nombre compris entre 0 et 1 024. |
| MinimumBuffers | Nombre minimal de mémoires tampons allouées pour le pool de mémoires tampons de la session de suivi des événements. | Entier positif supérieur ou égal à deux fois le nombre de cœurs logiques. |
| MaximumBuffers | Nombre maximal de mémoires tampons allouées pour le pool de mémoires tampons de la session de suivi des événements. | Nombre supérieur ou égal à MinimumBuffers. |
| JustMyCode | Spécifie la liste des répertoires Just My Code. | Liste de zéro, un ou plusieurs éléments MyCodeDirectory. |
| MyCodeDirectory | Spécifie un répertoire qui contient votre code. | Chemin absolu. |

### <a name="example"></a>Exemple  
 Au lieu de créer un fichier de configuration de toutes pièces, vous pouvez copier l’exemple suivant et le modifier en fonction de vos besoins.  

```xml  
<?xml version="1.0"?>  
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">  

  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>  

  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>  

  <TraceLocation>C:\traces</TraceLocation>  

  <SymbolPath>http://symweb</SymbolPath>  

  <Markers>  
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />  
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />  
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />  
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />  
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />  
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />  
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />  

    <!-- The IsEnabled and Categories elements are optional -->  
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />  
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />  
  </Markers>  

  <FilterConfig>  
    <CollectClrEvents>true</CollectClrEvents>  
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>  
    <CollectSampleEvents>true</CollectSampleEvents>  
    <CollectGpuEvents>true</CollectGpuEvents>  
    <CollectFileIO>true</CollectFileIO>  
  </FilterConfig>  

  <UserBufferSettings>  
    <BufferFlushTimer>0</BufferFlushTimer>  
    <BufferSize>256</BufferSize>  
    <MinimumBuffers>512</MinimumBuffers>  
    <MaximumBuffers>1024</MaximumBuffers>  
  </UserBufferSettings>  

  <KernelBufferSettings>  
    <BufferFlushTimer>0</BufferFlushTimer>  
    <BufferSize>256</BufferSize>  
    <MinimumBuffers>512</MinimumBuffers>  
    <MaximumBuffers>1024</MaximumBuffers>  
  </KernelBufferSettings>  

  <!-- List of MyCodeDirectory directories -->  
  <JustMyCode>  
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>  
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>  
  </JustMyCode>  
</LocalConfig>  

```
