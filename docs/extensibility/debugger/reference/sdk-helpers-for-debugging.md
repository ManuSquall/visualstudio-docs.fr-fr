---
title: Aides SDK pour Debugging (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edb7c508fdea6736a71c0f70c0d2ff305d4a399
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713651"
---
# <a name="sdk-helpers-for-debugging"></a>Programmes d’assistance SDK pour le débogage
Ces fonctions et déclarations sont des fonctions d’aide mondiales pour la mise en œuvre des moteurs de débogé, des évaluateurs d’expression et des fournisseurs de symboles dans le C.

> [!NOTE]
> Il n’existe actuellement aucune version gérée de ces fonctions et déclarations.

## <a name="overview"></a>Vue d'ensemble
 Pour que les moteurs déboçons, les évaluateurs d’expression et les fournisseurs de symboles soient utilisés par Visual Studio, ils doivent être enregistrés. Cela se fait en définissant des sous-clés et des entrées de registre, autrement appelées « mesures de réglage ». Les fonctions globales suivantes sont conçues pour faciliter le processus de mise à jour de ces mesures. Consultez la section sur les emplacements du registre pour connaître la disposition de chaque sous-clé de registre qui est mise à jour par ces fonctions.

## <a name="general-metric-functions"></a>Fonctions métriques générales
 Ce sont des fonctions générales utilisées par les moteurs de débogé. Les fonctions spécialisées pour les évaluateurs d’expression et les fournisseurs de symboles sont détaillées plus tard.

### <a name="getmetric-method"></a>Méthode GetMetric
 Récupère une valeur métrique du registre.

```cpp
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
|pszMachine|[dans] Nom d’une machine peut-être`NULL` distante dont le registre sera écrit (signifie machine locale).|
|pszType|[dans] Un des types métriques.|
|guidSection|[dans] GUID d’un moteur spécifique, évaluateur, exception, etc. Cela spécifie une sous-section sous un type métrique pour un élément spécifique.|
|pszMetric (en)|[dans] La mesure à obtenir. Cela correspond à un nom de valeur spécifique.|
|pdwValue|[dans] L’emplacement de stockage de la valeur de la mesure. Il existe plusieurs saveurs de GetMetric qui peuvent retourner un DWORD (comme dans cet exemple), un BSTR, un GUID, ou un tableau de GUIDs.|
|pszAltRoot|[dans] Une racine de registre alternatif à utiliser. Configurez pour `NULL` utiliser la valeur par défaut.|

### <a name="setmetric-method"></a>Méthode SetMetric
 Définit la valeur métrique spécifiée dans le registre.

```cpp
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
|pszType|[dans] Un des types métriques.|
|guidSection|[dans] GUID d’un moteur spécifique, évaluateur, exception, etc. Cela spécifie une sous-section sous un type métrique pour un élément spécifique.|
|pszMetric (en)|[dans] La mesure à obtenir. Cela correspond à un nom de valeur spécifique.|
|dwValue dwValue|[dans] L’emplacement de stockage de la valeur dans la métrique. Il existe plusieurs saveurs de SetMetric qui peuvent stocker un DWORD (dans cet exemple), un BSTR, un GUID, ou un tableau de GUIDs.|
|fUserSpecific|[dans] VRAI si la mesure est spécifique à l’utilisateur et si elle doit être écrite à la ruche de l’utilisateur au lieu de la ruche de la machine locale.|
|pszAltRoot|[dans] Une racine de registre alternatif à utiliser. Configurez pour `NULL` utiliser la valeur par défaut.|

### <a name="removemetric-method"></a>Supprimer la méthodemetric
 Supprime la mesure spécifiée du registre.

```cpp
HRESULT RemoveMetric(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   LPCWSTR pszAltRoot
);
```

|Paramètre|Description|
|---------------|-----------------|
|pszType|[dans] Un des types métriques.|
|guidSection|[dans] GUID d’un moteur spécifique, évaluateur, exception, etc. Cela spécifie une sous-section sous un type métrique pour un élément spécifique.|
|pszMetric (en)|[dans] La mesure à supprimer. Cela correspond à un nom de valeur spécifique.|
|pszAltRoot|[dans] Une racine de registre alternatif à utiliser. Configurez pour `NULL` utiliser la valeur par défaut.|

### <a name="enummetricsections-method"></a>Méthode EnumMetricSections
 énumère les différentes sections métriques du registre.

```cpp
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
|pszMachine|[dans] Nom d’une machine peut-être`NULL` distante dont le registre sera écrit (signifie machine locale).|
|pszType|[dans] Un des types métriques.|
|rgguidSections|[dans, dehors] Tableau préaffecté de GUIDs à remplir.|
|pdwSize|[dans] Le nombre maximum de GUID qui `rgguidSections` peuvent être stockés dans le tableau.|
|pszAltRoot|[dans] Une racine de registre alternatif à utiliser. Configurez pour `NULL` utiliser la valeur par défaut.|

## <a name="expression-evaluator-functions"></a>Fonctions d’évaluateur d’expression

|Fonction|Description|
|--------------|-----------------|
|GetEEMetric (en)|Récupère une valeur métrique du registre.|
|SetEEMetric (setEEMetric)|Définit la valeur métrique spécifiée dans le registre.|
|SupprimerEEMetric|Supprime la mesure spécifiée du registre.|
|GetEEMetricFile|Obtient un nom de fichier de la mesure spécifiée et le charge, le retour du contenu du fichier comme une chaîne.|

## <a name="exception-functions"></a>Fonctions d’exception

|Fonction|Description|
|--------------|-----------------|
|GetExceptionMetric (en anglais)|Récupère une valeur métrique du registre.|
|SetExceptionMetric|Définit la valeur métrique spécifiée dans le registre.|
|SupprimerExceptionMetric|Supprime la mesure spécifiée du registre.|
|SupprimerAllExceptionMetrics|Supprime toutes les mesures d’exception du registre.|

## <a name="symbol-provider-functions"></a>Fonctions de fournisseur de symboles

|Fonction|Description|
|--------------|-----------------|
|GetSPMetric (en)|Récupère une valeur métrique du registre.|
|SetSPMetric (setSPMetric)|Définit la valeur métrique spécifiée dans le registre.|
|SupprimerSPMetric|Supprime la mesure spécifiée du registre.|

## <a name="enumeration-functions"></a>Fonctions d’énumération

|Fonction|Description|
|--------------|-----------------|
|EnumMetricSections|Énumère toutes les mesures pour un type métrique spécifié.|
|EnumDebugEngine|Énumère les moteurs de débogés enregistrés.|
|EnumEEs|Énumère les évaluateurs d’expression enregistrés.|
|EnumExceptionMetrics (en anglais)|Énumère toutes les mesures d’exception.|

## <a name="metric-definitions"></a>Définitions de métriques
 Ces définitions peuvent être utilisées pour les noms métriques prédéfinis. Les noms correspondent à diverses clés de registre et noms de valeur `extern LPCWSTR metrictypeEngine`et sont tous définis comme des chaînes de caractère large: par exemple, .

|Types métriques prédéfinis|Description: La clé de base pour ....|
|-----------------------------|---------------------------------------|
|métriquetypeEngine|Toutes les mesures du moteur de débogé.|
|métriquePortSupplier|Toutes les mesures des fournisseurs portuaires.|
|métriquetException|Toutes les mesures d’exception.|
|métriquepeEEExtension|Toutes les extensions d’évaluateur d’expression.|

|Propriétés de moteur de de débogé|Description|
|-----------------------------|-----------------|
|métriqueAddressBP|Définissez-vous à nonzero pour indiquer la prise en charge des points d’arrêt d’adresse.|
|métriqueAlwaysLoadLocal|Réglé à nonzero afin de toujours charger le moteur de débog localement.|
|métriqueLoadInDebuggeeSession|NON UTILISÉ|
|métriqueLoadedByDebuggee|Réglé à nonzero pour indiquer que le moteur de débog sera toujours chargé avec ou par le programme étant déboisé.|
|métriqueAttach|Définissez-vous à nonzero pour indiquer le soutien à l’attachement aux programmes existants.|
|métriqueCallStackBP|Définissez-le à nonzero pour indiquer le support pour les points de rupture de pile d’appel.|
|métriqueConditionalBP|Définissez-le à nonzero pour indiquer le support pour le réglage des points de rupture conditionnels.|
|métriqueDataBP|Définissez-vous à nonzero pour indiquer la prise en charge de l’arrangement des points d’arrêt sur les modifications des données.|
|métriqueDisassembly|Réglé à nonzero pour indiquer le soutien à la production d’une liste de démontage.|
|métriqueDumpCrire|Réglé à nonzero pour indiquer le support pour l’écriture de décharge (le dumping de la mémoire à un dispositif de sortie).|
|métriqueENC|Définissez-vous à nonzero pour indiquer la prise en charge de Edit and Continue. **Note:**  Un moteur de débogé personnalisé ne doit jamais régler ceci ou devrait toujours le régler à 0.|
|métriqueExceptions|Définissez-le à nonzero pour indiquer le support des exceptions.|
|métriqueFunctionBP|Définissez-le à nonzero pour indiquer le support des points d’arrêt nommés (points de rupture qui se cassent lorsqu’un certain nom de fonction est appelé).|
|metricHitCountBP|Définissez-le à nonzero pour indiquer le support pour le réglage des points d’arrêt des « points d’arrêt » (points d’arrêt qui ne sont déclenchés qu’après avoir été touchés un certain nombre de fois).|
|métriqueJITDebug|Définissez-le à nonzero pour indiquer le soutien pour le débogage juste-à-temps (le débbuggeur est lancé quand une exception se produit dans un processus en cours d’exécution).|
|métriqueMemory|NON UTILISÉ|
|métriquePortSupplier|Définissez ceci au CLSID du fournisseur de port si l’on est mis en œuvre.|
|métriquesRegisters|NON UTILISÉ|
|metricSetNextStatement|Définissez à nonzero pour indiquer le support pour la définition de la déclaration suivante (qui saute l’exécution des déclarations intermédiaires).|
|metricSuspendThread|Réglez à nonzero pour indiquer le support pour suspendre l’exécution du fil.|
|métriqueWarnIfNoSymbols|Réglez à nonzero pour indiquer que l’utilisateur doit être informé s’il n’y a pas de symboles.|
|métriqueProgrammeProvider|Définissez ceci au CLSID du fournisseur de programme.|
|metricAlwaysLoadProgramProviderLocal|Réglez ceci à nonzero pour indiquer que le fournisseur de programme doit toujours être chargé localement.|
|métriqueEngineCanWatchProcess|Définissez ceci à nonzero pour indiquer que le moteur de débog surveillera pour des événements de processus au lieu du fournisseur de programme.|
|métriqueRemoteDebugging|Réglez ceci à nonzero pour indiquer le support pour le débogage à distance.|
|métriqueEncUseNativeBuilder|Réglez ceci à nonzero pour indiquer que le gestionnaire d’édition et de continuer devrait employer encbuild.dll du moteur de débagé pour construire pour Modifier et Continuer. **Note:**  Un moteur de débogé personnalisé ne doit jamais régler ceci ou devrait toujours le régler à 0.|
|métriqueLoadUnderWOW64|Réglez ceci à nonzero pour indiquer que le moteur de débaillement doit être chargé dans le processus de débagé sous WOW lors de débogage d’un processus de 64 bits ; sinon, le moteur de déboguer sera chargé dans le processus Visual Studio (qui fonctionne sous WOW64).|
|métriqueLoadProgramProviderUnderWOW64|Définissez ceci à nonzero pour indiquer que le fournisseur de programme doit être chargé dans le processus de débbuggee lors de débogage d’un processus de 64 bits sous WOW; autrement, il sera chargé dans le processus Visual Studio.|
|metricStopOnExceptionCrossingManagedBoundary|Définissez ceci à nonzero pour indiquer que le processus doit s’arrêter si une exception non manipulée est jetée à travers les limites de code gérées/non gérées.|
|métriqueAutoSelectPriority|Définissez cette priorité pour la sélection automatique du moteur de débogé (des valeurs plus élevées sont plus prioritaires).|
|metricAutoSelectIncompatibleList|Clé de registre contenant des entrées qui spécifient des GUIDs pour les moteurs de débogés à ignorer dans la sélection automatique. Ces entrées sont un nombre (0, 1, 2, et ainsi de suite) avec un GUID exprimé comme une chaîne.|
|metricIncompatibleList|Clé de registre contenant des entrées qui spécifient des GUIDs pour les moteurs débogés qui sont incompatibles avec ce moteur de débogé.|
|métriqueDisableJITOptimisation|Réglez ceci à nonzero pour indiquer que les optimisations juste-à-temps (pour le code géré) devraient être désactivées pendant le débogage.|

|Propriétés d’évaluateur d’expression|Description|
|-------------------------------------|-----------------|
|métriqueEngine|Cela tient le nombre de moteurs de débogé qui prennent en charge l’évaluateur d’expression spécifié.|
|métriquePreloadModules|Réglez ceci à nonzero pour indiquer que les modules doivent être préchargés lorsqu’un évaluateur d’expression est lancé contre un programme.|
|métriqueThisObjectName|Définissez ceci au nom de l’objet " cet objet .|

|Propriétés d’extension d’évaluateur d’expression|Description|
| - |-----------------|
|métriqueExtensionDll|Nom de la dll qui prend en charge cette extension.|
|métriqueExtensionLes inscriptionsSupported|Liste des registres pris en charge.|
|métriqueExtensionLes immatriculésEntryPoint|Point d’entrée pour accéder aux registres.|
|métriqueExtensionTypesSupported|Liste des types pris en charge.|
|métriqueExtensionTypesEntryPoint|Point d’entrée pour l’accès aux types.|

|Propriétés de fournisseur de porto|Description|
|------------------------------|-----------------|
|métriquePortPickerCLSID|Le CLSID du cueilleur de porto (une boîte de dialogue que l’utilisateur peut utiliser pour sélectionner les ports et ajouter des ports à utiliser pour le débogage).|
|métriqueDisallowUserEnteredPorts|Nonzero si les ports entrants par l’utilisateur ne peuvent pas être ajoutés au fournisseur du port (ce qui rend la boîte de dialogue port-picker essentiellement lu-seulement).|
|métriquePidBase|L’ID de processus de base utilisé par le fournisseur du port lors de l’attribution des pièces d’identité du processus.|

|Types de magasins SP prédéfinis|Description|
|-------------------------------|-----------------|
|storetypeFile|Les symboles sont stockés dans un fichier séparé.|
|storetypeMetadata|Les symboles sont stockés sous forme de métadonnées dans un assemblage.|

|Propriétés diverses|Description|
|------------------------------|-----------------|
|metricShowNonUserCode|Réglez ceci à nonzero pour afficher le code non-utiliser.|
|métriqueJustMyCodeStepping|Réglez ceci à nonzero pour indiquer que le pas ne peut se produire que dans le code utilisateur.|
|métriqueCLSID|CLSID pour un objet d’un type métrique spécifique.|
|metricName|Nom convivial pour un objet d’un type métrique spécifique.|
|métriqueLanguage|Nom de la langue.|

## <a name="registry-locations"></a>Emplacements de registre
 Les mesures sont lues et écrites au `VisualStudio` registre, en particulier dans le sous-clé.

> [!NOTE]
> La plupart du temps, les mesures seront écrites à la clé HKEY_LOCAL_MACHINE. Cependant, parfois, HKEY_CURRENT_USER sera la clé de destination. Dbgmetric.lib gère les deux touches. Lors de l’obtention d’une mesure, il recherche HKEY_CURRENT_USER d’abord, puis HKEY_LOCAL_MACHINE. Lorsqu’il est en train de définir une mesure, un paramètre précise la clé de haut niveau à utiliser.

 *[clé de registre]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[version racine]*\

 *[racine métrique]*\

 *[type métrique]*\

 *[métrique] - [valeur métrique]*

 *[métrique] - [valeur métrique]*

 *[métrique] - [valeur métrique]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[clé de registre]*|`HKEY_CURRENT_USER` ou `HKEY_LOCAL_MACHINE`.|
|*[version racine]*|La version de Visual Studio `7.0` `7.1`(par `8.0`exemple, , , ou ). Cependant, cette racine peut également être modifiée à l’aide du commutateur **/rootsuffix** à **devenv.exe**. Pour VSIP, ce modificateur est généralement **Exp**, de sorte que la racine de la version serait, par exemple, 8.0Exp.|
|*[racine métrique]*|C’est `AD7Metrics` `AD7Metrics(Debug)`soit ou , selon que la version de débog de dbgmetric.lib est utilisé. **Note:**  Que dbgmetric.lib soit utilisé ou non, cette convention de nommage doit être respectée si vous avez des différences entre les versions de débogé et de version qui doivent être reflétées dans le registre.|
|*[type métrique]*|Le type de mesure `Engine`à `ExpressionEvaluator` `SymbolProvider`écrire: , , , etc. Ceux-ci sont tous définis comme `metricTypeXXXX`dans `XXXX` dbgmetric.h comme , où est le nom de type spécifique.|
|*[métrique]*|Le nom d’une entrée à attribuer une valeur afin de définir la mesure. L’organisation réelle des mesures dépend du type métrique.|
|*[valeur métrique]*|La valeur attribuée à la mesure. Le type que la valeur doit avoir (corde, nombre, etc.) dépend de la mesure.|

> [!NOTE]
> Tous les GUID sont stockés dans le format de `{GUID}`. Par exemple : `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Moteurs Debug
 Ce qui suit est l’organisation des mesures des moteurs de débogé dans le registre. `Engine`est le nom de type métrique d’un moteur de débogé et correspond à *[type métrique]* dans le sous-arbre de registre ci-dessus.

 `Engine`\

 *[moteur guid]*\

 `CLSID` = *[classe guid]*

 *[métrique] - [valeur métrique]*

 *[métrique] - [valeur métrique]*

 *[métrique] - [valeur métrique]*

 `PortSupplier`\

 `0` = *[fournisseur de port guid]*

 `1` = *[fournisseur de port guid]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[moteur guid]*|Le GUID du moteur de débogé.|
|*[classe guid]*|Le GUID de la classe qui met en œuvre ce moteur débogé.|
|*[fournisseur de port guid]*|Le GUID du fournisseur du port, le cas échéant. De nombreux moteurs débogés utilisent le fournisseur de port par défaut et ne précisent donc pas leur propre fournisseur. Dans ce cas, `PortSupplier` le sous-clé sera absent.|

### <a name="port-suppliers"></a>Fournisseurs de ports
 Ce qui suit est l’organisation des mesures des fournisseurs portuaires dans le registre. `PortSupplier`est le nom de type métrique d’un fournisseur de port et correspond à *[type métrique]*.

 `PortSupplier`\

 *[fournisseur de port guid]*\

 `CLSID` = *[classe guid]*

 *[métrique] - [valeur métrique]*

 *[métrique] - [valeur métrique]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[fournisseur de port guid]*|Le GUID du fournisseur portuaire|
|*[classe guid]*|Le GUID de la classe qui met en œuvre ce fournisseur de ports|

### <a name="symbol-providers"></a>Fournisseurs de symboles
 Ce qui suit est l’organisation des mesures des fournisseurs de symboles dans le registre. `SymbolProvider`est le nom de type métrique pour le fournisseur de symboles et correspond à *[type métrique]*.

 `SymbolProvider`\

 *[fournisseur de symboles guid]*\

 `file`\

 `CLSID` = *[classe guid]*

 *[métrique] - [valeur métrique]*

 *[métrique] - [valeur métrique]*

 `metadata`\

 `CLSID` = *[classe guid]*

 *[métrique] - [valeur métrique]*

 *[métrique] - [valeur métrique]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[fournisseur de symboles guid]*|Le GUID du fournisseur de symboles|
|*[classe guid]*|Le GUID de la classe qui met en œuvre ce fournisseur de symboles|

### <a name="expression-evaluators"></a>Évaluateurs d’expression
 Ce qui suit est l’organisation des mesures d’évaluateur d’expression dans le registre. `ExpressionEvaluator`est le nom de type métrique de l’évaluateur d’expression et correspond à *[type métrique]*.

> [!NOTE]
> Le type `ExpressionEvaluator` métrique n’est pas défini en dbgmetric.h, car on suppose que tous les changements métriques `ExpressionEvaluator` pour les évaluateurs d’expression passeront par les fonctions métriques d’évaluateur d’expression appropriées (la disposition du sous-clé est quelque peu compliquée, de sorte que les détails sont cachés à l’intérieur dbgmetric.lib).

 `ExpressionEvaluator`\

 *[guid langue]*\

 *[vendeur guid]*\

 `CLSID` = *[classe guid]*

 *[métrique] - [valeur métrique]*

 *[métrique] - [valeur métrique]*

 `Engine`\

 `0` = *[débog moteur guid]*

 `1` = *[débog moteur guid]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[guid langue]*|Le GUID d’une langue|
|*[vendeur guid]*|Le GUID d’un vendeur|
|*[classe guid]*|Le GUID de la classe qui met en œuvre cet évaluateur d’expression|
|*[débog moteur guid]*|Le GUID d’un moteur de débogé que cet évaluateur d’expression travaille avec|

### <a name="expression-evaluator-extensions"></a>Extensions d’évaluateur d’expression
 Ce qui suit est l’organisation des mesures d’extension de l’évaluateur d’expression dans le registre. `EEExtensions`est le nom de type métrique pour les extensions d’évaluateur d’expression et correspond à *[type métrique]*.

 `EEExtensions`\

 *[extension guid]*\

 *[métrique] - [valeur métrique]*

 *[métrique] - [valeur métrique]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[extension guid]*|Le GUID d’une extension d’évaluateur d’expression|

### <a name="exceptions"></a>Exceptions
 Ce qui suit est l’organisation des mesures d’exception dans le registre. `Exception`est le nom de type métrique pour les exceptions et correspond à *[type métrique]*.

 `Exception`\

 *[débog moteur guid]*\

 *[types d’exception]*\

 *[exception]*\

 *[métrique] - [valeur métrique]*

 *[métrique] - [valeur métrique]*

 *[exception]*\

 *[métrique] - [valeur métrique]*

 *[métrique] - [valeur métrique]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[débog moteur guid]*|Le GUID d’un moteur de débogé qui prend en charge les exceptions.|
|*[types d’exception]*|Un titre général pour le sous-clé identifiant la classe d’exceptions qui peuvent être traitées. Les noms typiques sont **les exceptions de C,** **Win32 Exceptions**, Exceptions de course de langue **commune,** et **les contrôles de course-temps indigènes.** Ces noms sont également utilisés pour identifier une classe particulière d’exception à l’utilisateur.|
|*[exception]*|Un nom pour une exception : par exemple, **_com_error** ou **Control-Break**. Ces noms sont également utilisés pour identifier une exception particulière à l’utilisateur.|

## <a name="requirements"></a>Spécifications
 Ces fichiers sont [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] situés dans le répertoire d’installation SDK (par défaut, *[drive]*'Program\\Files’Microsoft Visual Studio 2010 SDK ).

 En-tête: inclut’dbgmetric.h

 Bibliothèque: libs-ad2de.lib, libs-dbgmetric.lib

## <a name="see-also"></a>Voir aussi
- [Référence des API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
