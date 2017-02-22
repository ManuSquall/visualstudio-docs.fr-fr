---
title: "&#171; Helpers &#187; du Kit de d&#233;veloppement logiciel pour le d&#233;bogage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dbgmetric.lib"
  - "Registre, le Kit de développement logiciel de débogage"
  - "Débogage du SDK, les emplacements du Registre"
  - "dbgmetric.h"
  - "mesures (débogage SDK)"
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# &#171; Helpers &#187; du Kit de d&#233;veloppement logiciel pour le d&#233;bogage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ces fonctions et déclarations sont des fonctions d'assistance globales pour implémenter des moteurs de débogage, les évaluateurs d'expression, et les fournisseurs de symbole en C\+\+.  
  
> [!NOTE]
>  Il n'existe aucune version managée de ces fonctions et déclarations de référence.  
  
## Vue d'ensemble  
 Pour que les moteurs de débogage, des évaluateurs d'expression, et les fournisseurs de symbole soient utilisés par Visual Studio, ils doivent être enregistrés.  Cela est fait en définissant des sous\-clés et des entrées de Registre, sinon appelées « métriques du paramètre. » Les fonctions globales suivantes sont conçues pour simplifier le processus de mise à jour ces métriques.  Consultez la section sur les emplacements de Registre pour découvrir la disposition de chaque sous\-clé de Registre qui est mise à jour par ces fonctions.  
  
## fonctions métriques générales  
 Ce sont des fonctions générales utilisées par les moteurs de débogage.  Les fonctions spécialisées pour les évaluateurs d'expression et des fournisseurs de symboles sont détaillées ultérieurement.  
  
### méthode de GetMetric  
 Récupère une valeur métrique du Registre.  
  
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
|pszMachine|\[in\]  le nom probablement d'un ordinateur distant dont le registre sera écrit \(`NULL` signifie l'ordinateur local\).|  
|pszType|\[in\]  L'un des types métriques.|  
|guidSection|\[in\]  GUID d'un moteur, d'un évaluateur, d'une exception, etc. spécifiques.  Cela spécifie une sous\-section sous un type métrique d'un élément spécifique.|  
|pszMetric|\[in\]  La métrique à obtenir.  Cela correspond à un nom de valeur spécifique.|  
|pdwValue|\[in\]  L'emplacement de stockage de la valeur de la métrique.  Il existe plusieurs versions de GetMetric qui peuvent retourner une valeur DWORD \(comme dans cet exemple\), un BSTR, un GUID, ou un tableau de GUID.|  
|pszAltRoot|\[in\]  Une autre racine de Registre à utiliser.  Affectez à `NULL` pour utiliser la valeur par défaut.|  
  
### méthode de SetMetric  
 Définit la valeur métriques spécifiée dans le Registre.  
  
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
|pszType|\[in\]  L'un des types métriques.|  
|guidSection|\[in\]  GUID d'un moteur, d'un évaluateur, d'une exception, etc. spécifiques.  Cela spécifie une sous\-section sous un type métrique d'un élément spécifique.|  
|pszMetric|\[in\]  La métrique à obtenir.  Cela correspond à un nom de valeur spécifique.|  
|dwValue|\[in\]  L'emplacement de stockage de la valeur dans la métrique.  Il existe plusieurs versions de SetMetric qui peuvent inscrire un DWORD \(dans cet exemple\), un BSTR, un GUID, ou un tableau de GUID.|  
|fUserSpecific|\[in\]  TRUE si la métrique est spécifique à l'utilisateur et s'il est écrit dans la ruche de l'utilisateur au lieu de la ruche de l'ordinateur local.|  
|pszAltRoot|\[in\]  Une autre racine de Registre à utiliser.  Affectez à `NULL` pour utiliser la valeur par défaut.|  
  
### méthode de RemoveMetric  
 Supprime la métrique spécifiée du Registre.  
  
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
|pszType|\[in\]  L'un des types métriques.|  
|guidSection|\[in\]  GUID d'un moteur, d'un évaluateur, d'une exception, etc. spécifiques.  Cela spécifie une sous\-section sous un type métrique d'un élément spécifique.|  
|pszMetric|\[in\]  La métrique à supprimer.  Cela correspond à un nom de valeur spécifique.|  
|pszAltRoot|\[in\]  Une autre racine de Registre à utiliser.  Affectez à `NULL` pour utiliser la valeur par défaut.|  
  
### méthode d'EnumMetricSections  
 énumère les différentes sections métriques dans le Registre.  
  
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
|pszMachine|\[in\]  le nom probablement d'un ordinateur distant dont le registre sera écrit \(`NULL` signifie l'ordinateur local\).|  
|pszType|\[in\]  L'un des types métriques.|  
|rgguidSections|\[in, out\]  Tableau pré\-allouée de GUID à accomplir.|  
|pdwSize|\[in\]  Le nombre maximal de GUID qui peut être enregistré dans le tableau d' `rgguidSections` .|  
|pszAltRoot|\[in\]  Une autre racine de Registre à utiliser.  Affectez à `NULL` pour utiliser la valeur par défaut.|  
  
## Fonctions évaluateur d'expression  
  
|Fonction|Description|  
|--------------|-----------------|  
|GetEEMetric|Récupère une valeur métrique du Registre.|  
|SetEEMetric|Définit la valeur métriques spécifiée dans le Registre.|  
|RemoveEEMetric|Supprime la métrique spécifiée du Registre.|  
|GetEEMetricFile|Obtient un nom de fichier de la métrique spécifié et la charge, en retournant le contenu du fichier en tant que chaîne.|  
  
## fonctions d'exception  
  
|Fonction|Description|  
|--------------|-----------------|  
|GetExceptionMetric|Récupère une valeur métrique du Registre.|  
|SetExceptionMetric|Définit la valeur métriques spécifiée dans le Registre.|  
|RemoveExceptionMetric|Supprime la métrique spécifiée du Registre.|  
|RemoveAllExceptionMetrics|Supprime toutes les métriques d'exception du Registre.|  
  
## fonctions de fournisseur de symbole  
  
|Fonction|Description|  
|--------------|-----------------|  
|GetSPMetric|Récupère une valeur métrique du Registre.|  
|SetSPMetric|Définit la valeur métriques spécifiée dans le Registre.|  
|RemoveSPMetric|Supprime la métrique spécifiée du Registre.|  
  
## fonctions d'énumération  
  
|Fonction|Description|  
|--------------|-----------------|  
|EnumMetricSections|Énumère toutes les métriques pour un type métriques spécifié.|  
|EnumDebugEngine|énumère les moteurs de débogage enregistrés.|  
|EnumEEs|énumère les évaluateurs d'expression enregistrés.|  
|EnumExceptionMetrics|Énumère toutes les métriques d'exception.|  
  
## définitions métriques  
 Ces définitions peuvent être utilisées pour les noms métriques prédéfinis.  Tous les noms correspondent à des clés de Registre et à noms de la valeur et sont définis comme des chaînes à caractères larges : par exemple, `extern LPCWSTR metrictypeEngine`.  
  
|types métriques prédéfinis|description : la clé de base pour….|  
|--------------------------------|-----------------------------------------|  
|metrictypeEngine|Toutes les métriques du moteur de débogage.|  
|metrictypePortSupplier|Tous passent des métriques de fournisseur.|  
|metrictypeException|Toutes les métriques d'exception.|  
|metricttypeEEExtension|Toutes les extensions évaluateur d'expression.|  
  
|Propriétés du moteur de débogage|Description|  
|--------------------------------------|-----------------|  
|metricAddressBP|Ayant une valeur différente de zéro pour indiquer la prise en charge des points d'arrêt sur adresse mémoire.|  
|metricAlwaysLoadLocal|Ayant une valeur différente de zéro afin de charger toujours le moteur de débogage localement.|  
|metricLoadInDebuggeeSession|NO UTILISÉ|  
|metricLoadedByDebuggee|Affectez une valeur différente de zéro pour indiquer que le moteur de débogage sera toujours chargée avec ou par le programme débogué.|  
|metricAttach|L'ensemble à une valeur différente de zéro pour indiquer la prise en charge de la pièce jointe à exister programme.|  
|metricCallStackBP|Ayant une valeur différente de zéro pour indiquer la prise en charge des points d'arrêt de la pile des appels.|  
|metricConditionalBP|Ayant une valeur différente de zéro pour indiquer la prise en charge du paramètre des points d'arrêt conditionnels.|  
|metricDataBP|Ayant une valeur différente de zéro pour indiquer la prise en charge du paramètre des points d'arrêt sur les modifications des données.|  
|metricDisassembly|Ayant une valeur différente de zéro pour indiquer la prise en charge de la production d'obtenir l'intégralité du code machine.|  
|metricDumpWriting|Ayant une valeur différente de zéro pour indiquer la prise en charge de l'écriture de dump \(faire un dump de la mémoire à un périphérique de sortie\).|  
|metricENC|Affectez une valeur différente de zéro pour indiquer la prise en charge de la modification et de continuer. **Note:**  Un moteur de débogage personnalisé ne doit jamais définir cela ou doit toujours le définir à 0.|  
|metricExceptions|Ayant une valeur différente de zéro pour indiquer la prise en charge des exceptions.|  
|metricFunctionBP|Ayant une valeur différente de zéro pour indiquer la prise en charge des points d'arrêt nommés \(points d'arrêt qui arrête lorsqu'une certaine nom de fonction est appelé\).|  
|metricHitCountBP|Ayant une valeur différente de zéro pour indiquer la prise en charge du paramètre des points d'arrêt « de point de correspondance » \(points d'arrêt qui sont déclenchés uniquement après est atteint un certain nombre de fois\).|  
|metricJITDebug|Ayant une valeur différente de zéro en signe en charge le débogage juste\-à\-temps \(le débogueur est lancé lorsqu'une exception se produit dans un processus en cours de exécution\).|  
|metricMemory|NO UTILISÉ|  
|metricPortSupplier|Affectez \-lui le CLSID du fournisseur de port s'il est implémenté.|  
|metricRegisters|NO UTILISÉ|  
|metricSetNextStatement|Ayant une valeur différente de zéro pour indiquer la prise en charge de définir l'instruction suivante \(qui ignore l'exécution des instructions intermédiaires\).|  
|metricSuspendThread|Ayant une valeur différente de zéro pour indiquer la prise en charge d'interrompre l'exécution des threads.|  
|metricWarnIfNoSymbols|Affectez une valeur différente de zéro pour indiquer qu'il doit être informé l'utilisateur s'il n'y a aucun symbole.|  
|metricProgramProvider|Affectez \-lui le CLSID du fournisseur de programme.|  
|metricAlwaysLoadProgramProviderLocal|Affectez \-lui une valeur différente de zéro pour indiquer que le fournisseur de programme doit toujours être chargé localement.|  
|metricEngineCanWatchProcess|Affectez \-lui une valeur différente de zéro pour indiquer que le moteur de débogage regardera alors pour les événements de processus au lieu du fournisseur de programme.|  
|metricRemoteDebugging|Affectez \-lui une valeur différente de zéro en signe en charge le débogage distant.|  
|metricEncUseNativeBuilder|Affectez \-lui une valeur différente de zéro pour indiquer que la modification et reprise du gestionnaire doit utiliser l'encbuild.dll du moteur de débogage pour générer pour la modification et de continuer. **Note:**  Un moteur de débogage personnalisé ne doit jamais définir cela ou doit toujours le définir à 0.|  
|metricLoadUnderWOW64|Affectez \-lui une valeur différente de zéro pour indiquer que le moteur de débogage doit être chargé dans le processus du programme débogué sous le WOW lors de le débogage d'un processus 64 bits ; sinon, le moteur de débogage sera chargé dans le processus Visual Studio \(qui s'exécute sous WOW64\).|  
|metricLoadProgramProviderUnderWOW64|Affectez \-lui une valeur différente de zéro pour indiquer que le fournisseur de programme doit être chargé dans le processus du programme débogué lors de le débogage d'un processus 64 bits sous le WOW ; sinon, il est chargé dans le processus Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Affectez \-lui une valeur différente de zéro pour indiquer que le processus doit arrêter si une exception non gérée est levée au delà de les limites managées\/code non managé.|  
|metricAutoSelectPriority|Affectez \-lui une priorité pour la sélection automatique du moteur de débogage \(les valeurs supérieures est égal à la priorité supérieure\).|  
|metricAutoSelectIncompatibleList|Clé de Registre contenant les entrées qui spécifient les GUID pour les moteurs de débogage sont ignorés dans la sélection automatique.  Ces entrées sont un nombre \(0, 1, 2, etc.\) avec un GUID exprimé sous la forme d'une chaîne.|  
|metricIncompatibleList|Clé de Registre contenant les entrées qui spécifient GUID pour les moteurs de débogage qui sont incompatibles avec ce moteur de débogage.|  
|metricDisableJITOptimization|Affectez \-lui une valeur différente de zéro pour indiquer que les optimisations juste\-à\-temps \(pour le code managé\) doivent être désactivées lors de le débogage.|  
  
|Propriétés évaluateur d'expression|Description|  
|----------------------------------------|-----------------|  
|metricEngine|Cela contient le nombre de moteurs de débogage qui prennent en charge l'évaluateur d'expression spécifié.|  
|metricPreloadModules|Affectez \-lui une valeur différente de zéro pour indiquer que les modules doivent être préchargés lorsqu'un évaluateur d'expression est lancé à un programme.|  
|metricThisObjectName|Définissez ce paramètre en « this » nom de l'objet.|  
  
|Propriétés d'extension évaluateur d'expression|Description|  
|----------------------------------------------------|-----------------|  
|metricExtensionDll|Nom de la DLL qui prend en charge cette extension.|  
|metricExtensionRegistersSupported|liste de registres pris en charge.|  
|metricExtensionRegistersEntryPoint|Point d'entrée pour les registres accès.|  
|metricExtensionTypesSupported|liste de types pris en charge.|  
|metricExtensionTypesEntryPoint|Point d'entrée pour les types d'accès.|  
  
|propriétés de fournisseur de port|Description|  
|---------------------------------------|-----------------|  
|metricPortPickerCLSID|Le CLSID de le sélecteur de port \(une boîte de dialogue que l'utilisateur peut sélectionner des ports et d'ajouter des ports à utiliser pour le débogage\).|  
|metricDisallowUserEnteredPorts|Une valeur différente de zéro si les ports utilisateur\-entrés ne peuvent pas être ajoutés au fournisseur de port \(cela rend la boîte de dialogue de port\-récolteuse essentiellement en lecture seule\).|  
|metricPidBase|L'ID de processus de base utilisé par le fournisseur de port en allouant les ID de processus.|  
  
|Types prédéfinis du magasin de SP|Description|  
|---------------------------------------|-----------------|  
|storetypeFile|Les symboles sont stockés dans un fichier séparé.|  
|storetypeMetadata|Les symboles sont stockés sous forme de métadonnées dans un assembly.|  
  
|Diverses propriétés|Description|  
|-------------------------|-----------------|  
|metricShowNonUserCode|Affectez \-lui une valeur différente de zéro pour afficher le code non\-utilisateur.|  
|metricJustMyCodeStepping|Affectez \-lui une valeur différente de zéro pour indiquer que le pas \- à \- pas peut se produire uniquement dans le code utilisateur.|  
|metricCLSID|Le CLSID pour un objet d'un type métriques spécifique.|  
|metricName|Nom convivial d'un objet d'un type métriques spécifique.|  
|metricLanguage|Nom de la langue.|  
  
## emplacements de Registre  
 Les mesures sont lues à partir de et écrites dans le Registre, en particulier dans la sous\-clé d' `VisualStudio` .  
  
> [!NOTE]
>  Le plus souvent, la métrique sera entrée à la clé HKEY\_LOCAL\_MACHINE.  Toutefois, il arrive que HKEY\_CURRENT\_USER est la clé de destination.  Dbgmetric.lib traite les deux clés.  En obtenant un métriques, il recherche HKEY\_CURRENT\_USER d'abord, puis HKEY\_LOCAL\_MACHINE.  Lorsqu'il définit un métriques, un paramètre spécifie quelle clé de niveau supérieur à utiliser.  
  
 *\[clé de Registre\]*\\  
  
 `Software`\\  
  
 `Microsoft`\\  
  
 `VisualStudio`\\  
  
 *\[racine de version\]*\\  
  
 *\[racine métriques\]*\\  
  
 *\[type métriques\]*\\  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
|Espace réservé|Description|  
|--------------------|-----------------|  
|*\[clé de Registre\]*|`HKEY_CURRENT_USER` ou `HKEY_LOCAL_MACHINE`.|  
|*\[racine de version\]*|la version de Visual Studio \(par exemple, `7.0`, `7.1`, ou `8.0`\).  Toutefois, cette racine peut également être modifiée à l'aide de le commutateur d'**\/rootsuffix** à **devenv.exe**.  Pour VSIP, ce modificateur est généralement Exp, donc la racine de version est, par exemple, 8.0Exp.|  
|*\[racine métriques\]*|c'est ou `AD7Metrics` ou `AD7Metrics(Debug)`, selon que la version debug de dbgmetric.lib est utilisé. **Note:**  Si dbgmetric.lib est utilisé, cette convention d'affectation de noms doit être adhérée si vous avez des différences entre les versions debug et Release qui doivent être pris en compte dans le Registre.|  
|*\[type métriques\]*|Le type de la métrique à écrire : `Engine`, `ExpressionEvaluator`, `SymbolProvider`, etc.  Ils sont tous sont définis comme dans dbgmetric.h comme, où est le nom spécifique de type.|  
|*\[métriques\]*|Le nom d'une entrée pour assigner une valeur pour définir la métrique.  l'organisation réelle de la métrique dépend du type métrique.|  
|*\[valeur métriques\]*|la valeur assignée au métrique.  Le type que la valeur doit avoir \(chaîne, nombre, etc.\). dépend de la métrique.|  
  
> [!NOTE]
>  Tout le GUID sont stockés dans le format d' `{GUID}`.  Par exemple, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### moteurs de débogage  
 Voici l'organisation de la métrique de moteurs de débogage dans le Registre.  `Engine` est le nom de type métrique d'un moteur de débogage et correspond à *\[type métriques\]* dans la sous\-arborescence ci\-dessus de Registre.  
  
 `Engine`\\  
  
 *\[guid du moteur\]*\\  
  
 `CLSID` \= *\[guid de classe\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 `PortSupplier`\\  
  
 `0` \= *\[guid de fournisseur de port\]*  
  
 `1` \= *\[guid de fournisseur de port\]*  
  
|Espace réservé|Description|  
|--------------------|-----------------|  
|*\[guid du moteur\]*|GUID du moteur de débogage.|  
|*\[guid de classe\]*|GUID de la classe qui implémente ce moteur de débogage.|  
|*\[guid de fournisseur de port\]*|GUID du fournisseur de port le cas échéant.  De nombreuses moteurs de débogage utilisent le fournisseur de port par défaut et ne spécifient pas leur propre fournisseur.  Dans ce cas, la sous\-clé `PortSupplier` est absente.|  
  
### déplacez les fournisseurs  
 Voici l'organisation de la métrique de fournisseur de port dans le Registre.  `PortSupplier` est le nom de type métrique d'un fournisseur de port et correspond à *\[type métriques\]*.  
  
 `PortSupplier`\\  
  
 *\[guid de fournisseur de port\]*\\  
  
 `CLSID` \= *\[guid de classe\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
|Espace réservé|Description|  
|--------------------|-----------------|  
|*\[guid de fournisseur de port\]*|GUID du fournisseur de port|  
|*\[guid de classe\]*|GUID de la classe qui implémente ce fournisseur de port|  
  
### fournisseurs de symbole  
 Voici l'organisation de la métrique de fournisseur de symbole dans le Registre.  `SymbolProvider` est le nom de type métrique du fournisseur de symbole et correspond à *\[type métriques\]*.  
  
 `SymbolProvider`\\  
  
 *\[guid de fournisseur de symbole\]*\\  
  
 `file`\\  
  
 `CLSID` \= *\[guid de classe\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 `metadata`\\  
  
 `CLSID` \= *\[guid de classe\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
|Espace réservé|Description|  
|--------------------|-----------------|  
|*\[guid de fournisseur de symbole\]*|GUID du fournisseur de symbole|  
|*\[guid de classe\]*|GUID de la classe qui implémente ce fournisseur de symbole|  
  
### évaluateurs d'expression  
 Voici l'organisation de la métrique évaluateur d'expression dans le Registre.  `ExpressionEvaluator` est le nom de type métrique pour l'évaluateur d'expression et correspond à *\[type métriques\]*.  
  
> [!NOTE]
>  Le type mesures de `ExpressionEvaluator` n'est pas défini dans dbgmetric.h, car il est supposé que toutes les modifications métriques pour les évaluateurs d'expression aboutissent via les fonctions métriques évaluateur d'expression approprié \(la disposition de la sous\-clé d' `ExpressionEvaluator` est quelque peu complexe, les détails sont masqués à l'intérieur de dbgmetric.lib\).  
  
 `ExpressionEvaluator`\\  
  
 *\[guid de langage\]*\\  
  
 *\[guid de fournisseur\]*\\  
  
 `CLSID` \= *\[guid de classe\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 `Engine`\\  
  
 `0` \= *\[guid du moteur de débogage\]*  
  
 `1` \= *\[guid du moteur de débogage\]*  
  
|Espace réservé|Description|  
|--------------------|-----------------|  
|*\[guid de langage\]*|GUID d'un langage|  
|*\[guid de fournisseur\]*|GUID d'un fournisseur|  
|*\[guid de classe\]*|GUID de la classe qui implémente l'évaluateur d'expression|  
|*\[guid du moteur de débogage\]*|GUID d'un moteur de débogage avec lequel cet évaluateur d'expression fonctionne|  
  
### Extensions évaluateur d'expression  
 Voici l'organisation de la métrique d'extension évaluateur d'expression dans le Registre.  `EEExtensions` est le nom de type métrique pour les extensions évaluateur d'expression et correspond à *\[type métriques\]*.  
  
 `EEExtensions`\\  
  
 *\[guid d'extension\]*\\  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
|Espace réservé|Description|  
|--------------------|-----------------|  
|*\[guid d'extension\]*|GUID d'une extension évaluateur d'expression|  
  
### Exceptions  
 Voici l'organisation de la métrique d'exceptions dans le Registre.  `Exception` est le nom de type métrique pour les exceptions et correspond à *\[type métriques\]*.  
  
 `Exception`\\  
  
 *\[guid du moteur de débogage\]*\\  
  
 *\[types d'exceptions\]*\\  
  
 *\[exception\]*\\  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[exception\]*\\  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
 *\[métriques\] \= \[valeur métriques\]*  
  
|Espace réservé|Description|  
|--------------------|-----------------|  
|*\[guid du moteur de débogage\]*|GUID d'un moteur de débogage qui prend en charge des exceptions.|  
|*\[types d'exceptions\]*|Un titre général pour la sous\-clé identifiant la classe de les gérer.  Les noms classiques sont **C\+\+ Exceptions**, **Win32 Exceptions**, **Common Language Runtime Exceptions**, et **Native Run\-Time Checks**.  ces noms sont également utilisés pour identifier une classe particulière d'exception à l'utilisateur.|  
|*\[exception\]*|un nom pour une exception : par exemple, **\_com\_error** ou **Control\-Break**.  ces noms sont également utilisés pour identifier une exception particulière à l'utilisateur.|  
  
## Configuration requise  
 Ces fichiers se trouvent dans le répertoire d'installation de [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] Kit de développement logiciel \(par défaut, *\[lecteur\]*\\Program Files\\Microsoft Visual Studio 2010 SDK \\\).  
  
 en\-tête : inclut \\ dbgmetric.h  
  
 bibliothèque : bibliothèques \\ ad2de.lib, bibliothèques \\ dbgmetric.lib  
  
## Voir aussi  
 [Référence API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)