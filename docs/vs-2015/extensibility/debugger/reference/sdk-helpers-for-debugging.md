---
title: Aides SDK pour le débogage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 904ac14433bf6b7b839a4fe634175a7f583e27ab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772181"
---
# <a name="sdk-helpers-for-debugging"></a>Programmes d’assistance SDK pour le débogage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ces fonctions et les déclarations sont des fonctions d’assistance globales pour l’implémentation des moteurs de débogage, les évaluateurs d’expression et les fournisseurs de symbole dans C++.  
  
> [!NOTE]
>  Il n’existe aucune version managée de ces fonctions et les déclarations pour l’instant.  
  
## <a name="overview"></a>Vue d'ensemble  
 Dans l’ordre pour les moteurs de débogage, les évaluateurs d’expression et les fournisseurs de symbole à utiliser par Visual Studio, ils doivent être inscrits. Cela est effectué en définissant des sous-clés de Registre et des entrées, également appelées « mesures de paramètre ». Les fonctions globales suivantes sont conçues pour faciliter le processus de mise à jour de ces mesures. Consultez la section sur les emplacements du Registre pour déterminer la disposition de chaque sous-clé de Registre est mis à jour par ces fonctions.  
  
## <a name="general-metric-functions"></a>Fonctions de mesure générales  
 Il s’agit des fonctions générales utilisées par les moteurs de débogage. Des fonctions spécialisées pour les évaluateurs d’expression et les fournisseurs de symbole sont détaillées plus loin.  
  
### <a name="getmetric-method"></a>GetMetric (méthode)  
 Récupère une valeur métrique à partir du Registre.  
  
```cpp#  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Paramètre|Description|  
|---------------|-----------------|  
|pszMachine|[in] Nom d’un ordinateur à distance dont register écraseront (`NULL` signifie l’ordinateur local).|  
|strType Argument|[in] Un des types de métriques.|  
|guidSection|[in] GUID de moteur spécifique, d’évaluateur, exception, etc. Spécifie une sous-section sous un type de mesure pour un élément spécifique.|  
|pszMetric|[in] La mesure doit être obtenu. Cela correspond à un nom de valeur spécifique.|  
|pdwValue|[in] L’emplacement de stockage de la valeur de la métrique. Il existe plusieurs types de GetMetric qui peut retourner une valeur DWORD (comme dans cet exemple), un BSTR, un GUID ou un tableau de GUID.|  
|pszAltRoot|[in] Une racine de Registre de remplacement à utiliser. La valeur `NULL` à utiliser la valeur par défaut.|  
  
### <a name="setmetric-method"></a>SetMetric (méthode)  
 Définit la valeur de métrique spécifiée dans le Registre.  
  
```cpp#  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Paramètre|Description|  
|---------------|-----------------|  
|strType Argument|[in] Un des types de métriques.|  
|guidSection|[in] GUID de moteur spécifique, d’évaluateur, exception, etc. Spécifie une sous-section sous un type de mesure pour un élément spécifique.|  
|pszMetric|[in] La mesure doit être obtenu. Cela correspond à un nom de valeur spécifique.|  
|dwValue|[in] L’emplacement de stockage de la valeur dans la mesure. Il existe plusieurs types de SetMetric capable de stocker une valeur DWORD (dans cet exemple), un BSTR, un GUID ou un tableau de GUID.|  
|fUserSpecific|[in] TRUE si la métrique est spécifique à l’utilisateur et si elle doit être écrit dans la ruche de l’utilisateur au lieu de la ruche de l’ordinateur local.|  
|pszAltRoot|[in] Une racine de Registre de remplacement à utiliser. La valeur `NULL` à utiliser la valeur par défaut.|  
  
### <a name="removemetric-method"></a>RemoveMetric (méthode)  
 Supprime la mesure spécifiée à partir du Registre.  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Paramètre|Description|  
|---------------|-----------------|  
|strType Argument|[in] Un des types de métriques.|  
|guidSection|[in] GUID de moteur spécifique, d’évaluateur, exception, etc. Spécifie une sous-section sous un type de mesure pour un élément spécifique.|  
|pszMetric|[in] La métrique à supprimer. Cela correspond à un nom de valeur spécifique.|  
|pszAltRoot|[in] Une racine de Registre de remplacement à utiliser. La valeur `NULL` à utiliser la valeur par défaut.|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections (méthode)  
 Énumère les différentes sections de métrique dans le Registre.  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Paramètre|Description|  
|---------------|-----------------|  
|pszMachine|[in] Nom d’un ordinateur à distance dont register écraseront (`NULL` signifie l’ordinateur local).|  
|strType Argument|[in] Un des types de métriques.|  
|rgguidSections|[in, out] Tableau préalloué de GUID doit être renseigné.|  
|pdwSize|[in] Le nombre maximal de GUID qui peuvent être stockées dans le `rgguidSections` tableau.|  
|pszAltRoot|[in] Une racine de Registre de remplacement à utiliser. La valeur `NULL` à utiliser la valeur par défaut.|  
  
## <a name="expression-evaluator-functions"></a>Fonctions évaluateur d’expression  
  
|Fonction|Description|  
|--------------|-----------------|  
|GetEEMetric|Récupère une valeur métrique à partir du Registre.|  
|SetEEMetric|Définit la valeur de métrique spécifiée dans le Registre.|  
|RemoveEEMetric|Supprime la mesure spécifiée à partir du Registre.|  
|GetEEMetricFile|Obtient un nom de fichier à partir de la mesure spécifiée et la charge, en retournant le contenu du fichier sous forme de chaîne.|  
  
## <a name="exception-functions"></a>Fonctions de l’exception  
  
|Fonction|Description|  
|--------------|-----------------|  
|GetExceptionMetric|Récupère une valeur métrique à partir du Registre.|  
|SetExceptionMetric|Définit la valeur de métrique spécifiée dans le Registre.|  
|RemoveExceptionMetric|Supprime la mesure spécifiée à partir du Registre.|  
|RemoveAllExceptionMetrics|Supprime toutes les métriques de l’exception à partir du Registre.|  
  
## <a name="symbol-provider-functions"></a>Fonctions de fournisseur de symboles  
  
|Fonction|Description|  
|--------------|-----------------|  
|GetSPMetric|Récupère une valeur métrique à partir du Registre.|  
|SetSPMetric|Définit la valeur de métrique spécifiée dans le Registre.|  
|RemoveSPMetric|Supprime la mesure spécifiée à partir du Registre.|  
  
## <a name="enumeration-functions"></a>Fonctions d’énumération  
  
|Fonction|Description|  
|--------------|-----------------|  
|EnumMetricSections|Énumère toutes les métriques pour un type de mesure spécifié.|  
|EnumDebugEngine|Énumère les moteurs de débogage inscrits.|  
|EnumEEs|Énumère les évaluateurs d’expression inscrit.|  
|EnumExceptionMetrics|Énumère toutes les métriques de l’exception.|  
  
## <a name="metric-definitions"></a>Définitions de métrique  
 Ces définitions peuvent être utilisées pour les noms des mesures prédéfinies. Les noms correspondent aux différentes clés de Registre et les noms de valeur et sont tous définis en tant que chaînes de caractères larges : par exemple, `extern LPCWSTR metrictypeEngine`.  
  
|Types de mesure prédéfinies|Description : La clé de base pour...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Toutes les mesures du moteur de débogage.|  
|metrictypePortSupplier|Toutes les métriques de fournisseur de port.|  
|metrictypeException|Toutes les mesures de l’exception.|  
|metricttypeEEExtension|Toutes les extensions d’évaluateur d’expression.|  
  
|Propriétés du moteur de débogage|Description|  
|-----------------------------|-----------------|  
|metricAddressBP|La valeur est différente de zéro pour indiquer la prise en charge des points d’arrêt de l’adresse.|  
|metricAlwaysLoadLocal|La valeur est différente de zéro pour toujours charger le moteur de débogage localement.|  
|metricLoadInDebuggeeSession|NON UTILISÉ|  
|metricLoadedByDebuggee|La valeur est différente de zéro pour indiquer que le moteur de débogage est toujours chargé avec ou par le programme en cours de débogage.|  
|metricAttach|La valeur est différente de zéro pour indiquer la prise en charge des pièces jointes pour les programmes existants.|  
|metricCallStackBP|La valeur est différente de zéro pour indiquer la prise en charge des points d’arrêt de la pile des appels.|  
|metricConditionalBP|La valeur est différente de zéro pour indiquer la prise en charge pour la définition de points d’arrêt conditionnels.|  
|metricDataBP|La valeur est différente de zéro pour indiquer la prise en charge pour le paramètre des points d’arrêt sur les modifications apportées aux données.|  
|metricDisassembly|Définir à différente de zéro pour indiquer la prise en charge pour la production d’une liste de code machine.|  
|metricDumpWriting|La valeur est différente de zéro pour indiquer la prise en charge pour le vidage d’écriture (du vidage de mémoire à un périphérique de sortie).|  
|metricENC|Définir à différente de zéro pour indiquer la prise en charge par Modifier & Continuer. **Remarque :** un moteur de débogage personnalisé ne doit jamais défini cela ou doit toujours définie sur 0.|  
|metricExceptions|La valeur est différente de zéro pour indiquer la prise en charge pour les exceptions.|  
|metricFunctionBP|La valeur est différente de zéro pour indiquer la prise en charge des points d’arrêt nommées (points d’arrêt qui s’arrêtent lorsqu’un certain nom de fonction est appelé).|  
|metricHitCountBP|La valeur est différente de zéro pour indiquer la prise en charge pour le paramètre des points d’arrêt « point d’accès » (points d’arrêt qui sont déclenchés uniquement une fois atteint un certain nombre de fois).|  
|metricJITDebug|Définir à différente de zéro pour indiquer la prise en charge pour le débogage juste-à-temps (le débogueur est lancé lorsqu’une exception se produit dans un processus en cours d’exécution).|  
|metricMemory|NON UTILISÉ|  
|metricPortSupplier|Définissez ce paramètre sur le CLSID du fournisseur de port si elle est implémentée.|  
|metricRegisters|NON UTILISÉ|  
|metricSetNextStatement|La valeur est différente de zéro pour indiquer la prise en charge de la définition de l’instruction suivante (qui ignore l’exécution d’instructions intermédiaires).|  
|metricSuspendThread|La valeur est différente de zéro pour indiquer la prise en charge de la suspension de l’exécution du thread.|  
|metricWarnIfNoSymbols|La valeur est différente de zéro pour indiquer que l’utilisateur doit être informé si aucun symbole n’y.|  
|metricProgramProvider|Définissez ce paramètre sur le CLSID du fournisseur de programme.|  
|metricAlwaysLoadProgramProviderLocal|Définissez cette valeur à différente de zéro pour indiquer que le fournisseur du programme doit toujours être chargé localement.|  
|metricEngineCanWatchProcess|Affectez la valeur différente de zéro pour indiquer que le moteur de débogage surveillera pour traiter les événements au lieu du fournisseur du programme.|  
|metricRemoteDebugging|Affectez la valeur différente de zéro pour indiquer la prise en charge pour le débogage distant.|  
|metricEncUseNativeBuilder|Définissez cette valeur à différente de zéro pour indiquer que le modifier et continuer le gestionnaire doivent utiliser encbuild.dll du moteur débogage pour générer pour modifier & Continuer. **Remarque :** un moteur de débogage personnalisé ne doit jamais défini cela ou doit toujours définie sur 0.|  
|metricLoadUnderWOW64|Affectez la valeur différente de zéro pour indiquer que le moteur de débogage doit être chargé dans le processus du programme débogué sous WOW lors du débogage d’un processus 64 bits. Sinon, le moteur de débogage est chargé dans le processus de Visual Studio (qui s’exécute sous WOW64).|  
|metricLoadProgramProviderUnderWOW64|Affectez la valeur différente de zéro pour indiquer que le fournisseur du programme doit être chargé dans le processus du programme débogué lors du débogage d’un processus 64 bits sous WOW ; Sinon, elle est chargée dans le processus de Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Affectez la valeur différente de zéro pour indiquer que le processus doit s’arrêter si une exception non gérée est levée au-delà des limites de code non managé.|  
|metricAutoSelectPriority|Définissez ce paramètre sur une priorité pour la sélection automatique du moteur de débogage (priorité plus élevée valeurs equals plus élevée).|  
|metricAutoSelectIncompatibleList|Clé de Registre contenant des entrées qui spécifient les GUID des moteurs de débogage doivent être ignorés dans la sélection automatique. Ces entrées sont un nombre (0, 1, 2 et ainsi de suite) avec un GUID exprimé sous forme de chaîne.|  
|metricIncompatibleList|Clé de Registre contenant des entrées qui spécifient les GUID pour les moteurs de débogage ne sont pas compatibles avec ce moteur de débogage.|  
|metricDisableJITOptimization|Affectez la valeur différente de zéro pour indiquer que les optimisations juste-à-temps (pour le code managé) doivent être désactivées pendant le débogage.|  
  
|Propriétés évaluateur d’expression|Description|  
|-------------------------------------|-----------------|  
|metricEngine|Il conserve le nombre de moteurs de débogage qui prennent en charge de l’évaluateur d’expression spécifiée.|  
|metricPreloadModules|Affectez la valeur différente de zéro pour indiquer que les modules doivent être préchargées lorsqu’un évaluateur d’expression est exécutée sur un programme.|  
|metricThisObjectName|Définissez ce paramètre sur le nom d’objet « this ».|  
  
|Propriétés d’Extension évaluateur expression|Description|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Nom de la dll qui prend en charge de cette extension.|  
|metricExtensionRegistersSupported|Liste des registres pris en charge.|  
|metricExtensionRegistersEntryPoint|Point d’entrée pour l’accès aux registres.|  
|metricExtensionTypesSupported|Liste des types pris en charge.|  
|metricExtensionTypesEntryPoint|Point d’entrée pour accéder aux types.|  
  
|Propriétés de fournisseur de port|Description|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|Le CLSID du sélecteur de port (une boîte de dialogue l’utilisateur peut utiliser pour sélectionner des ports et ajouter des ports à utiliser pour le débogage).|  
|metricDisallowUserEnteredPorts|Différent de zéro si les ports entré par l’utilisateur ne peut pas être ajoutés pour le fournisseur de port (cela s’effectue dans la boîte de dialogue de sélecteur de port essentiellement en lecture seule).|  
|metricPidBase|L’ID de processus de base utilisé par le fournisseur de port lors de l’allocation d’ID de processus.|  
  
|Types de Store SP prédéfinis|Description|  
|-------------------------------|-----------------|  
|storetypeFile|Les symboles sont stockés dans un fichier distinct.|  
|storetypeMetadata|Les symboles sont stockés en tant que métadonnées dans un assembly.|  
  
|Autres propriétés.|Description|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Affectez la valeur différente de zéro pour afficher le code de non-utilisateur.|  
|metricJustMyCodeStepping|Affectez la valeur différente de zéro pour indiquer que pas à pas détaillé peut se produire uniquement dans le code utilisateur.|  
|metricCLSID|CLSID d’un objet d’un type de métrique spécifique.|  
|MetricName|Nom convivial pour un objet d’un type de métrique spécifique.|  
|metricLanguage|Nom de la langue.|  
  
## <a name="registry-locations"></a>Emplacements du Registre  
 Les mesures sont lues et écrites dans le Registre, en particulier dans le `VisualStudio` sous-clé.  
  
> [!NOTE]
>  La plupart du temps, les mesures seront écrites à la clé HKEY_LOCAL_MACHINE. Cependant, parfois HKEY_CURRENT_USER sera la clé de destination. Dbgmetric.lib gère les deux clés. Lors de l’obtention d’une mesure, il recherche HKEY_CURRENT_USER en premier, puis HKEY_LOCAL_MACHINE. Lorsqu’il configure une mesure, un paramètre spécifie la clé de niveau supérieur à utiliser.  
  
 *[clé de Registre]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[racine version]*\  
  
 *[métrique racine]*\  
  
 *[type de métrique]*\  
  
 *[métrique] = [valeur métrique]*  
  
 *[métrique] = [valeur métrique]*  
  
 *[métrique] = [valeur métrique]*  
  
|Espace réservé|Description|  
|-----------------|-----------------|  
|*[clé de Registre]*|`HKEY_CURRENT_USER` ou `HKEY_LOCAL_MACHINE`.|  
|*[racine version]*|La version de Visual Studio (par exemple, `7.0`, `7.1`, ou `8.0`). Toutefois, cette racine peut également être modifiée à l’aide de la **/rootsuffix** basculer vers **devenv.exe**. VSIP, ce modificateur est généralement pour **Exp**, de sorte que la racine de la version serait, par exemple, 8.0Exp.|  
|*[métrique racine]*|Il s’agit soit `AD7Metrics` ou `AD7Metrics(Debug)`, selon que la version debug de dbgmetric.lib est utilisée. **Remarque :** si dbgmetric.lib est utilisé, cette convention d’affectation de noms doit être respectée si vous avez des différences entre debug et release versions doivent être reflétées dans le Registre.|  
|*[type de métrique]*|Le type de mesure à écrire : `Engine`, `ExpressionEvaluator`, `SymbolProvider`, etc. Ceux-ci sont définis comme dans dbgmetric.h comme `metricTypeXXXX`, où `XXXX` est le nom de type spécifique.|  
|*[métrique]*|Le nom d’une entrée à assigner une valeur pour définir la métrique. L’organisation des mesures varie selon le type de mesure.|  
|*[valeur métrique]*|La valeur assignée à la métrique. Le type de que la valeur doit être (string), nombre, etc. dépend de la mesure.|  
  
> [!NOTE]
>  Tous les GUID sont stockés au format `{GUID}`. Par exemple, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Moteurs de débogage  
 Voici l’organisation des métriques de moteurs de débogage dans le Registre. `Engine` est le nom de type de métrique pour un moteur de débogage et correspond à *[type de métrique]* dans la sous-arborescence de Registre ci-dessus.  
  
 `Engine`\  
  
 *[guid de moteur]*\  
  
 `CLSID` = *[guid de classe]*  
  
 *[métrique] = [valeur métrique]*  
  
 *[métrique] = [valeur métrique]*  
  
 *[métrique] = [valeur métrique]*  
  
 `PortSupplier`\  
  
 `0` = *[guid de fournisseur de port]*  
  
 `1` = *[guid de fournisseur de port]*  
  
|Espace réservé|Description|  
|-----------------|-----------------|  
|*[guid de moteur]*|Le GUID du moteur de débogage.|  
|*[guid de classe]*|Le GUID de la classe qui implémente ce moteur de débogage.|  
|*[guid de fournisseur de port]*|GUID du fournisseur de port, le cas échéant. De nombreux moteurs de débogage utilisent le fournisseur de port par défaut et par conséquent, ne spécifient pas leur propre fournisseur. Dans ce cas, la sous-clé `PortSupplier` apparaîtra.|  
  
### <a name="port-suppliers"></a>Fournisseurs de ports  
 Voici l’organisation des métriques de fournisseur de port dans le Registre. `PortSupplier` est le nom de type de métrique pour un fournisseur de port et correspond à *[type de métrique]*.  
  
 `PortSupplier`\  
  
 *[guid de fournisseur de port]*\  
  
 `CLSID` = *[guid de classe]*  
  
 *[métrique] = [valeur métrique]*  
  
 *[métrique] = [valeur métrique]*  
  
|Espace réservé|Description|  
|-----------------|-----------------|  
|*[guid de fournisseur de port]*|Le GUID du fournisseur de port|  
|*[guid de classe]*|Le GUID de la classe qui implémente ce fournisseur de port|  
  
### <a name="symbol-providers"></a>Fournisseurs de symbole  
 Voici l’organisation des métriques de fournisseur de symboles dans le Registre. `SymbolProvider` est le nom de type de mesure pour le fournisseur de symboles et correspond à *[type de métrique]*.  
  
 `SymbolProvider`\  
  
 *[guid de fournisseur de symboles]*\  
  
 `file`\  
  
 `CLSID` = *[guid de classe]*  
  
 *[métrique] = [valeur métrique]*  
  
 *[métrique] = [valeur métrique]*  
  
 `metadata`\  
  
 `CLSID` = *[guid de classe]*  
  
 *[métrique] = [valeur métrique]*  
  
 *[métrique] = [valeur métrique]*  
  
|Espace réservé|Description|  
|-----------------|-----------------|  
|*[guid de fournisseur de symboles]*|Le GUID du fournisseur de symboles|  
|*[guid de classe]*|Le GUID de la classe qui implémente ce fournisseur de symboles|  
  
### <a name="expression-evaluators"></a>Évaluateurs d’expression  
 Voici l’organisation des métriques d’évaluateur d’expression dans le Registre. `ExpressionEvaluator` est le nom de type de mesure pour l’évaluateur d’expression et correspond à *[type de métrique]*.  
  
> [!NOTE]
>  Le type de mesure pour `ExpressionEvaluator` n’est pas défini dans dbgmetric.h, il est supposé que toutes les modifications des métriques pour les évaluateurs d’expression passera par les fonctions de métrique évaluateur expression appropriée (la disposition de la `ExpressionEvaluator` sous-clé est quelque peu compliquée, donc les détails sont masqués à l’intérieur de dbgmetric.lib).  
  
 `ExpressionEvaluator`\  
  
 *[langage guid]*\  
  
 *[guid de fournisseur]*\  
  
 `CLSID` = *[guid de classe]*  
  
 *[métrique] = [valeur métrique]*  
  
 *[métrique] = [valeur métrique]*  
  
 `Engine`\  
  
 `0` = *[guid du moteur de débogage]*  
  
 `1` = *[guid du moteur de débogage]*  
  
|Espace réservé|Description|  
|-----------------|-----------------|  
|*[langage guid]*|Le GUID d’une langue|  
|*[guid de fournisseur]*|Le GUID d’un fournisseur|  
|*[guid de classe]*|Le GUID de la classe qui implémente cette évaluateur d’expression|  
|*[guid du moteur de débogage]*|Le GUID d’un moteur de débogage fonctionnant avec cette évaluateur d’expression|  
  
### <a name="expression-evaluator-extensions"></a>Extensions d’évaluateur d’expression  
 Voici l’organisation des mesures expression évaluateur extension dans le Registre. `EEExtensions` est le nom de type de mesure pour l’expression à extensions d’évaluateur et correspond à *[type de métrique]*.  
  
 `EEExtensions`\  
  
 *[guid de l’extension]*\  
  
 *[métrique] = [valeur métrique]*  
  
 *[métrique] = [valeur métrique]*  
  
|Espace réservé|Description|  
|-----------------|-----------------|  
|*[guid de l’extension]*|Le GUID d’une extension d’évaluateur d’expression|  
  
### <a name="exceptions"></a>Exceptions  
 Voici l’organisation des mesures d’exceptions dans le Registre. `Exception` est le nom de type de métrique pour les exceptions et correspond à *[type de métrique]*.  
  
 `Exception`\  
  
 *[guid du moteur de débogage]*\  
  
 *[types d’exception]*\  
  
 *[exception]*\  
  
 *[métrique] = [valeur métrique]*  
  
 *[métrique] = [valeur métrique]*  
  
 *[exception]*\  
  
 *[métrique] = [valeur métrique]*  
  
 *[métrique] = [valeur métrique]*  
  
|Espace réservé|Description|  
|-----------------|-----------------|  
|*[guid du moteur de débogage]*|GUID du moteur de débogage qui prend en charge des exceptions.|  
|*[types d’exception]*|Un titre général pour la sous-clé qui identifie la classe d’exceptions qui peuvent être gérés. Les noms par défaut sont **Exceptions C++**, **Exceptions Win32**, **Exceptions Common Language Runtime**, et **Native Run-Time Checks**. Ces noms sont également utilisés pour identifier une classe d’exception à l’utilisateur particulière.|  
|*[exception]*|Un nom pour une exception : par exemple, **_com_error** ou **contrôle d’interruption**. Ces noms sont également utilisés pour identifier une exception spécifique à l’utilisateur.|  
  
## <a name="requirements"></a>Configuration requise  
 Ces fichiers se trouvent dans le [!INCLUDE[vs_dev10_ext](../../../includes/vs-dev10-ext-md.md)] répertoire d’installation de kit de développement logiciel (par défaut, *[lecteur]* \Program Files\Microsoft Visual Studio 2010 SDK\\).  
  
 En-tête : includes\dbgmetric.h  
  
 Bibliothèque : libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)

