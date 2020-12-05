---
title: Applications auxiliaires du kit de développement logiciel (SDK) pour le débogage | Microsoft Docs
description: En savoir plus sur les fonctions et les déclarations qui sont des fonctions d’assistance globales pour l’implémentation de moteurs de débogage, d’évaluateur d’expression et de fournisseurs de symboles en C++.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 32d0dd7dbeee70b8c4eb566a07cf9a44d40d4f49
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606539"
---
# <a name="sdk-helpers-for-debugging"></a>Programmes d’assistance SDK pour le débogage
Ces fonctions et déclarations sont des fonctions d’assistance globales pour l’implémentation de moteurs de débogage, d’évaluateur d’expression et de fournisseurs de symboles en C++.

> [!NOTE]
> Il n’existe aucune version managée de ces fonctions et déclarations pour l’instant.

## <a name="overview"></a>Vue d’ensemble
 Pour que les moteurs de débogage, les évaluateurs d’expression et les fournisseurs de symboles soient utilisés par Visual Studio, ils doivent être inscrits. Pour ce faire, vous définissez les sous-clés et les entrées de Registre, également appelées « paramètres des mesures ». Les fonctions globales suivantes sont conçues pour faciliter le processus de mise à jour de ces métriques. Consultez la section sur les emplacements du Registre pour connaître la disposition de chaque sous-clé de Registre mise à jour par ces fonctions.

## <a name="general-metric-functions"></a>Fonctions de métrique générales
 Il s’agit des fonctions générales utilisées par les moteurs de débogage. Des fonctions spécialisées pour les évaluateurs d’expression et les fournisseurs de symboles sont détaillées ultérieurement.

### <a name="getmetric-method"></a>Méthode GetMetric
 Récupère une valeur de métrique à partir du Registre.

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
|pszMachine|dans Nom d’un ordinateur éventuellement distant dont le Registre est écrit ( `NULL` c’est-à-dire ordinateur local).|
|pszType|dans Un des types de mesures.|
|guidSection|dans GUID d’un moteur, d’un évaluateur, d’une exception spécifique, etc. Cela spécifie une sous-section sous un type de mesure pour un élément spécifique.|
|pszMetric|dans Métrique à obtenir. Cela correspond à un nom de valeur spécifique.|
|pdwValue|dans Emplacement de stockage de la valeur de la métrique. Il existe plusieurs types de GetMetric qui peuvent retourner une valeur DWORD (comme dans cet exemple), un BSTR, un GUID ou un tableau de GUID.|
|pszAltRoot|dans Autre racine du Registre à utiliser. Affectez `NULL` la valeur pour utiliser la valeur par défaut.|

### <a name="setmetric-method"></a>Méthode SetMetric
 Définit la valeur de métrique spécifiée dans le registre.

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
|pszType|dans Un des types de mesures.|
|guidSection|dans GUID d’un moteur, d’un évaluateur, d’une exception spécifique, etc. Cela spécifie une sous-section sous un type de mesure pour un élément spécifique.|
|pszMetric|dans Métrique à obtenir. Cela correspond à un nom de valeur spécifique.|
|dwValue|dans Emplacement de stockage de la valeur dans la mesure. Il existe plusieurs types de SetMetric qui peuvent stocker une valeur DWORD (dans cet exemple), un BSTR, un GUID ou un tableau de GUID.|
|fUserSpecific|dans TRUE si la métrique est spécifique à l’utilisateur et si elle doit être écrite dans la ruche de l’utilisateur et non dans la ruche de l’ordinateur local.|
|pszAltRoot|dans Autre racine du Registre à utiliser. Affectez `NULL` la valeur pour utiliser la valeur par défaut.|

### <a name="removemetric-method"></a>Méthode RemoveMetric
 Supprime la mesure spécifiée du Registre.

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
|pszType|dans Un des types de mesures.|
|guidSection|dans GUID d’un moteur, d’un évaluateur, d’une exception spécifique, etc. Cela spécifie une sous-section sous un type de mesure pour un élément spécifique.|
|pszMetric|dans Métrique à supprimer. Cela correspond à un nom de valeur spécifique.|
|pszAltRoot|dans Autre racine du Registre à utiliser. Affectez `NULL` la valeur pour utiliser la valeur par défaut.|

### <a name="enummetricsections-method"></a>Méthode EnumMetricSections
 Énumère les différentes sections métriques du Registre.

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
|pszMachine|dans Nom d’un ordinateur éventuellement distant dont le Registre est écrit ( `NULL` c’est-à-dire ordinateur local).|
|pszType|dans Un des types de mesures.|
|rgguidSections|[in, out] Tableau de GUID préalloué à remplir.|
|pdwSize|dans Nombre maximal de GUID qui peuvent être stockés dans le `rgguidSections` tableau.|
|pszAltRoot|dans Autre racine du Registre à utiliser. Affectez `NULL` la valeur pour utiliser la valeur par défaut.|

## <a name="expression-evaluator-functions"></a>Fonctions de l’évaluateur d’expression

|Fonction|Description|
|--------------|-----------------|
|GetEEMetric|Récupère une valeur de métrique à partir du Registre.|
|SetEEMetric|Définit la valeur de métrique spécifiée dans le registre.|
|RemoveEEMetric|Supprime la mesure spécifiée du Registre.|
|GetEEMetricFile|Obtient un nom de fichier à partir de la métrique spécifiée et le charge, en retournant le contenu du fichier sous la forme d’une chaîne.|

## <a name="exception-functions"></a>Fonctions d’exception

|Fonction|Description|
|--------------|-----------------|
|GetExceptionMetric|Récupère une valeur de métrique à partir du Registre.|
|SetExceptionMetric|Définit la valeur de métrique spécifiée dans le registre.|
|RemoveExceptionMetric|Supprime la mesure spécifiée du Registre.|
|RemoveAllExceptionMetrics|Supprime toutes les mesures d’exception du Registre.|

## <a name="symbol-provider-functions"></a>Fonctions du fournisseur de symboles

|Fonction|Description|
|--------------|-----------------|
|GetSPMetric|Récupère une valeur de métrique à partir du Registre.|
|SetSPMetric|Définit la valeur de métrique spécifiée dans le registre.|
|RemoveSPMetric|Supprime la mesure spécifiée du Registre.|

## <a name="enumeration-functions"></a>Fonctions d’énumération

|Fonction|Description|
|--------------|-----------------|
|EnumMetricSections|Énumère toutes les métriques pour un type de métrique spécifié.|
|EnumDebugEngine|Énumère les moteurs de débogage inscrits.|
|EnumEEs|Énumère les évaluateurs d’expression inscrits.|
|EnumExceptionMetrics|Énumère toutes les mesures d’exception.|

## <a name="metric-definitions"></a>Définitions de métriques
 Ces définitions peuvent être utilisées pour les noms de métriques prédéfinis. Les noms correspondent à plusieurs clés de Registre et noms de valeurs, et sont tous définis comme des chaînes de caractères larges : par exemple, `extern LPCWSTR metrictypeEngine` .

|Types de métriques prédéfinis|Description : la clé de base pour...|
|-----------------------------|---------------------------------------|
|metrictypeEngine|Toutes les métriques du moteur de débogage.|
|metrictypePortSupplier|Toutes les métriques du fournisseur de port.|
|metrictypeException|Toutes les mesures d’exception.|
|metricttypeEEExtension|Toutes les extensions de l’évaluateur d’expression.|

|Propriétés du moteur de débogage|Description|
|-----------------------------|-----------------|
|metricAddressBP|Défini sur une valeur différente de zéro pour indiquer la prise en charge des points d’arrêt d’adresse.|
|metricAlwaysLoadLocal|Définissez sur une valeur différente de zéro pour toujours charger le moteur de débogage localement.|
|metricLoadInDebuggeeSession|NON UTILISÉ|
|metricLoadedByDebuggee|Définissez sur une valeur différente de zéro pour indiquer que le moteur de débogage sera toujours chargé avec ou par le programme en cours de débogage.|
|metricAttach|Défini sur une valeur différente de zéro pour indiquer la prise en charge des pièces jointes aux programmes existants.|
|metricCallStackBP|Défini sur une valeur différente de zéro pour indiquer la prise en charge des points d’arrêt de pile des appels.|
|metricConditionalBP|Défini sur une valeur différente de zéro pour indiquer la prise en charge de la définition des points d’arrêt conditionnels.|
|metricDataBP|Défini sur une valeur différente de zéro pour indiquer la prise en charge de la définition de points d’arrêt sur les modifications de données.|
|metricDisassembly|Défini sur une valeur différente de zéro pour indiquer la prise en charge de la production d’une liste de code machine.|
|metricDumpWriting|Défini sur une valeur différente de zéro pour indiquer la prise en charge de l’écriture de vidage (vidage de la mémoire sur un périphérique de sortie).|
|metricENC|Défini sur une valeur différente de zéro pour indiquer la prise en charge de modifier & continuer. **Remarque :**  Un moteur de débogage personnalisé ne doit jamais définir cette valeur ou doit toujours lui affecter la valeur 0.|
|metricExceptions|Défini sur une valeur différente de zéro pour indiquer la prise en charge des exceptions.|
|metricFunctionBP|Défini sur une valeur différente de zéro pour indiquer la prise en charge des points d’arrêt nommés (points d’arrêt qui s’arrêtent lorsqu’un certain nom de fonction est appelé).|
|metricHitCountBP|Défini sur une valeur différente de zéro pour indiquer la prise en charge du paramètre des points d’arrêt « point d’accès » (points d’arrêt déclenchés uniquement après un certain nombre de fois).|
|metricJITDebug|Défini sur une valeur différente de zéro pour indiquer la prise en charge du débogage juste-à-temps (le débogueur est lancé quand une exception se produit dans un processus en cours d’exécution).|
|metricMemory|NON UTILISÉ|
|metricPortSupplier|Définissez cette valeur sur le CLSID du fournisseur de port, le cas échéant.|
|metricRegisters|NON UTILISÉ|
|metricSetNextStatement|Défini sur une valeur différente de zéro pour indiquer la prise en charge de la définition de l’instruction suivante (qui ignore l’exécution des instructions intermédiaires).|
|metricSuspendThread|Défini sur une valeur différente de zéro pour indiquer la prise en charge de l’interruption de l’exécution des threads.|
|metricWarnIfNoSymbols|Définissez sur une valeur différente de zéro pour indiquer que l’utilisateur doit être averti s’il n’y a aucun symbole.|
|metricProgramProvider|Définissez cette valeur sur le CLSID du fournisseur du programme.|
|metricAlwaysLoadProgramProviderLocal|Définissez cette valeur sur une valeur différente de zéro pour indiquer que le fournisseur du programme doit toujours être chargé localement.|
|metricEngineCanWatchProcess|Définissez ce qui est différent de zéro pour indiquer que le moteur de débogage surveillera les événements de processus au lieu du fournisseur du programme.|
|metricRemoteDebugging|Définissez cette valeur sur une valeur différente de zéro pour indiquer la prise en charge du débogage distant.|
|metricEncUseNativeBuilder|Définissez cette valeur sur une valeur différente de zéro pour indiquer que le gestionnaire de modification et de continuation doit utiliser le encbuild.dll du moteur de débogage pour effectuer une génération pour modifier & continuer. **Remarque :**  Un moteur de débogage personnalisé ne doit jamais définir cette valeur ou doit toujours lui affecter la valeur 0.|
|metricLoadUnderWOW64|Affectez-lui une valeur différente de zéro pour indiquer que le moteur de débogage doit être chargé dans le processus du programme débogué sous WOW lors du débogage d’un processus 64 bits ; dans le cas contraire, le moteur de débogage sera chargé dans le processus Visual Studio (qui s’exécute sous WOW64).|
|metricLoadProgramProviderUnderWOW64|Définissez cette valeur sur une valeur différente de zéro pour indiquer que le fournisseur du programme doit être chargé dans le processus du programme débogué lors du débogage d’un processus 64 bits sous WOW ; dans le cas contraire, il sera chargé dans le processus Visual Studio.|
|metricStopOnExceptionCrossingManagedBoundary|Affectez-lui une valeur différente de zéro pour indiquer que le processus doit s’arrêter si une exception non gérée est levée dans les limites du code managé/non managé.|
|metricAutoSelectPriority|Définissez cette option sur une priorité pour la sélection automatique du moteur de débogage (les valeurs supérieures sont supérieures à la priorité).|
|metricAutoSelectIncompatibleList|Clé de registre contenant les entrées qui spécifient les GUID pour les moteurs de débogage à ignorer dans la sélection automatique. Ces entrées sont un nombre (0, 1, 2, etc.) avec un GUID exprimé sous la forme d’une chaîne.|
|metricIncompatibleList|Clé de registre contenant des entrées qui spécifient des GUID pour les moteurs de débogage qui ne sont pas compatibles avec ce moteur de débogage.|
|metricDisableJITOptimization|Définissez cette valeur sur une valeur différente de zéro pour indiquer que les optimisations juste-à-temps (pour le code managé) doivent être désactivées pendant le débogage.|

|Propriétés de l’évaluateur d’expression|Description|
|-------------------------------------|-----------------|
|metricEngine|Cela contient le nombre de moteurs de débogage qui prennent en charge l’évaluateur d’expression spécifié.|
|metricPreloadModules|Définissez cette valeur sur une valeur différente de zéro pour indiquer que les modules doivent être préchargés lorsqu’un évaluateur d’expression est lancé sur un programme.|
|metricThisObjectName|Définissez cette valeur sur le nom de l’objet « This ».|

|Propriétés d’extension de l’évaluateur d’expression|Description|
| - |-----------------|
|metricExtensionDll|Nom de la dll qui prend en charge cette extension.|
|metricExtensionRegistersSupported|Liste des registres pris en charge.|
|metricExtensionRegistersEntryPoint|Point d’entrée pour l’accès aux registres.|
|metricExtensionTypesSupported|Liste des types pris en charge.|
|metricExtensionTypesEntryPoint|Point d’entrée pour l’accès aux types.|

|Propriétés du fournisseur de port|Description|
|------------------------------|-----------------|
|metricPortPickerCLSID|CLSID du sélecteur de port (boîte de dialogue que l’utilisateur peut utiliser pour sélectionner des ports et ajouter des ports à utiliser pour le débogage).|
|metricDisallowUserEnteredPorts|Différent de zéro si les ports entrés par l’utilisateur ne peuvent pas être ajoutés au fournisseur de port (cela fait en sorte que la boîte de dialogue Sélecteur de port soit en lecture seule).|
|metricPidBase|ID de processus de base utilisé par le fournisseur de port lors de l’allocation des ID de processus.|

|Types de magasins SP prédéfinis|Description|
|-------------------------------|-----------------|
|storetypeFile|Les symboles sont stockés dans un fichier séparé.|
|storetypeMetadata|Les symboles sont stockés sous forme de métadonnées dans un assembly.|

|Propriétés diverses|Description|
|------------------------------|-----------------|
|metricShowNonUserCode|Définissez cette valeur sur une valeur différente de zéro pour afficher le code non-utilisateur.|
|metricJustMyCodeStepping|Définissez cette valeur sur une valeur différente de zéro pour indiquer que l’exécution pas à pas ne peut se produire que dans le code utilisateur.|
|metricCLSID|CLSID pour un objet d’un type de mesure spécifique.|
|metricName|Nom convivial pour un objet d’un type de mesure spécifique.|
|metricLanguage|Nom de la langue.|

## <a name="registry-locations"></a>Emplacements du Registre
 Les métriques sont lues et écrites dans le registre, en particulier dans la `VisualStudio` sous-clé.

> [!NOTE]
> La plupart du temps, les métriques sont écrites dans la clé de HKEY_LOCAL_MACHINE. Toutefois, HKEY_CURRENT_USER sera parfois la clé de destination. Dbgmetric. lib gère les deux clés. Lors de l’obtention d’une mesure, il recherche HKEY_CURRENT_USER d’abord, puis HKEY_LOCAL_MACHINE. Lorsqu’il définit une mesure, un paramètre spécifie la clé de niveau supérieur à utiliser.

 *[clé de Registre]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[racine de la version]*\

 *[racine métrique]*\

 *[type de mesure]*\

 *[metric] = [valeur métrique]*

 *[metric] = [valeur métrique]*

 *[metric] = [valeur métrique]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[clé de Registre]*|`HKEY_CURRENT_USER` ou `HKEY_LOCAL_MACHINE`.|
|*[racine de la version]*|Version de Visual Studio (par exemple,, `7.0` `7.1` ou `8.0` ). Toutefois, cette racine peut également être modifiée à l’aide du commutateur **/rootsuffix** pour **devenv.exe**. Pour VSIP, ce modificateur est généralement **exp**, donc la racine de la version est, par exemple, 8.0 exp.|
|*[racine métrique]*|Il s’agit `AD7Metrics` `AD7Metrics(Debug)` de ou, selon que la version de débogage de dbgmetric. lib est utilisée ou non. **Remarque :**  Que dbgmetric. lib soit utilisé ou non, cette Convention d’affectation de noms doit être respectée si vous avez des différences entre les versions Debug et Release qui doivent être reflétées dans le registre.|
|*[type de mesure]*|Type de métrique à écrire : `Engine` , `ExpressionEvaluator` , `SymbolProvider` , etc. Ils sont tous définis comme dans dbgmetric. h sous `metricTypeXXXX` la forme, où `XXXX` est le nom du type spécifique.|
|*critères*|Nom d’une entrée à laquelle une valeur doit être affectée pour définir la métrique. L’organisation réelle des métriques dépend du type de mesure.|
|*[valeur métrique]*|Valeur assignée à la mesure. Le type que la valeur doit avoir (chaîne, nombre, etc.) dépend de la métrique.|

> [!NOTE]
> Tous les GUID sont stockés au format `{GUID}` . Par exemple : `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Déboguer les moteurs
 L’Organisation des métriques de moteur de débogage dans le Registre est la suivante : `Engine` nom du type de mesure pour un moteur de débogage et correspond à *[metric type]* dans la sous-arborescence du Registre ci-dessus.

 `Engine`\

 *[GUID du moteur]*\

 `CLSID` = *[GUID de classe]*

 *[metric] = [valeur métrique]*

 *[metric] = [valeur métrique]*

 *[metric] = [valeur métrique]*

 `PortSupplier`\

 `0` = *[GUID du fournisseur de port]*

 `1` = *[GUID du fournisseur de port]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[GUID du moteur]*|GUID du moteur de débogage.|
|*[GUID de classe]*|GUID de la classe qui implémente ce moteur de débogage.|
|*[GUID du fournisseur de port]*|GUID du fournisseur de port, le cas échéant. De nombreux moteurs de débogage utilisent le fournisseur de port par défaut et ne spécifient donc pas leur propre fournisseur. Dans ce cas, la sous-clé `PortSupplier` est absente.|

### <a name="port-suppliers"></a>Fournisseurs de ports
 L’Organisation des métriques de fournisseur de port dans le Registre est la suivante : `PortSupplier` nom du type de mesure d’un fournisseur de ports et correspond à *[metric type]*.

 `PortSupplier`\

 *[GUID du fournisseur de port]*\

 `CLSID` = *[GUID de classe]*

 *[metric] = [valeur métrique]*

 *[metric] = [valeur métrique]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[GUID du fournisseur de port]*|GUID du fournisseur de port|
|*[GUID de classe]*|GUID de la classe qui implémente ce fournisseur de port|

### <a name="symbol-providers"></a>Fournisseurs de symboles
 Voici l’Organisation des métriques de fournisseur de symboles dans le registre. `SymbolProvider` nom du type de mesure pour le fournisseur de symboles et correspond à *[metric type]*.

 `SymbolProvider`\

 *[GUID du fournisseur de symboles]*\

 `file`\

 `CLSID` = *[GUID de classe]*

 *[metric] = [valeur métrique]*

 *[metric] = [valeur métrique]*

 `metadata`\

 `CLSID` = *[GUID de classe]*

 *[metric] = [valeur métrique]*

 *[metric] = [valeur métrique]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[GUID du fournisseur de symboles]*|GUID du fournisseur de symboles|
|*[GUID de classe]*|GUID de la classe qui implémente ce fournisseur de symboles|

### <a name="expression-evaluators"></a>Évaluateur d’expression
 Voici l’Organisation des métriques de l’évaluateur d’expression dans le registre. `ExpressionEvaluator` nom du type de mesure pour l’évaluateur d’expression et correspond à *[metric type]*.

> [!NOTE]
> Le type de mesure pour `ExpressionEvaluator` n’est pas défini dans dbgmetric. h, car il est supposé que toutes les modifications de métriques pour les évaluateurs d’expression vont traverser les fonctions de métrique de l’évaluateur d’expression appropriées (la disposition de la `ExpressionEvaluator` sous-clé est quelque peu compliquée, les détails sont donc masqués dans dbgmetric. lib).

 `ExpressionEvaluator`\

 *[GUID de langage]*\

 *[GUID du fournisseur]*\

 `CLSID` = *[GUID de classe]*

 *[metric] = [valeur métrique]*

 *[metric] = [valeur métrique]*

 `Engine`\

 `0` = *[GUID du moteur de débogage]*

 `1` = *[GUID du moteur de débogage]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[GUID de langage]*|GUID d’une langue|
|*[GUID du fournisseur]*|GUID d’un fournisseur|
|*[GUID de classe]*|GUID de la classe qui implémente cet évaluateur d’expression.|
|*[GUID du moteur de débogage]*|GUID d’un moteur de débogage que cet évaluateur d’expression utilise|

### <a name="expression-evaluator-extensions"></a>Extensions de l’évaluateur d’expression
 Voici l’Organisation des métriques d’extension de l’évaluateur d’expression dans le registre. `EEExtensions` nom du type de mesure pour les extensions de l’évaluateur d’expression et correspond à *[metric type]*.

 `EEExtensions`\

 *[GUID d’extension]*\

 *[metric] = [valeur métrique]*

 *[metric] = [valeur métrique]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[GUID d’extension]*|GUID d’une extension de l’évaluateur d’expression|

### <a name="exceptions"></a>Exceptions
 Voici l’Organisation des métriques d’exceptions dans le registre. `Exception` nom du type de mesure pour les exceptions et correspond à *[metric type]*.

 `Exception`\

 *[GUID du moteur de débogage]*\

 *[types d’exception]*\

 *titre*\

 *[metric] = [valeur métrique]*

 *[metric] = [valeur métrique]*

 *titre*\

 *[metric] = [valeur métrique]*

 *[metric] = [valeur métrique]*

|Espace réservé|Description|
|-----------------|-----------------|
|*[GUID du moteur de débogage]*|GUID d’un moteur de débogage qui prend en charge les exceptions.|
|*[types d’exception]*|Titre général pour la sous-clé identifiant la classe des exceptions qui peuvent être gérées. Les noms typiques sont les exceptions **C++**, les **Exceptions Win32**, les **exceptions du Common Language Runtime** et les **contrôles de Run-Time natifs**. Ces noms sont également utilisés pour identifier une classe particulière d’exception pour l’utilisateur.|
|*titre*|Nom d’une exception : par exemple, **_com_error** ou **un arrêt de contrôle**. Ces noms sont également utilisés pour identifier une exception particulière pour l’utilisateur.|

## <a name="requirements"></a>Configuration requise
 Ces fichiers se trouvent dans le [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] répertoire d’installation du kit de développement logiciel (SDK) (par défaut, *[lecteur]* \Program Files\Microsoft Visual Studio 2010 SDK \\ ).

 En-tête : includes\dbgmetric.h

 Bibliothèque : libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>Voir aussi
- [Référence sur l’API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
