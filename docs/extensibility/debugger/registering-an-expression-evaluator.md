---
title: Inscription d’un évaluateur d’expression | Microsoft Docs
description: Découvrez comment l’évaluateur d’expression doit s’inscrire lui-même en tant que fabrique de classe avec l’environnement COM Windows et Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f26eddf7191ee4393dd2ca986fe7a1d2c3af9e2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847141"
---
# <a name="register-an-expression-evaluator"></a>Inscrire un évaluateur d’expression
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’évaluateur d’expression (EE) doit s’inscrire en tant que fabrique de classe avec l’environnement COM Windows et Visual Studio. Une EE est configurée en tant que DLL afin d’être injectée dans l’espace d’adressage du moteur DE débogage (DE) ou dans l’espace d’adressage DE Visual Studio, en fonction de l’entité qui instancie le EE.

## <a name="managed-code-expression-evaluator"></a>Évaluateur d’expression de code managé
 Un code managé EE est implémenté comme une bibliothèque de classes, qui est une DLL qui s’inscrit auprès de l’environnement COM, généralement démarrée par un appel au programme VSIP, *regpkg.exe*. Le processus réel d’écriture des clés de Registre pour l’environnement COM est géré automatiquement.

 Une méthode de la classe principale est marquée avec <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> , ce qui indique que la méthode doit être appelée lorsque la dll est inscrite auprès de com. Cette méthode d’inscription, souvent appelée `RegisterClass` , exécute la tâche d’inscription de la dll auprès de Visual Studio. Un correspondant `UnregisterClass` (marqué avec <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> ), annule les effets de `RegisterClass` la désinstallation de la dll.
Les mêmes entrées de Registre sont effectuées comme pour un EE écrit dans du code non managé. la seule différence réside dans le fait qu’il n’existe aucune fonction d’assistance telle que `SetEEMetric` pour effectuer le travail pour vous. Voici un exemple de processus d’inscription et de désinscription.

### <a name="example"></a> Exemple
 La fonction suivante montre comment un code managé EE s’inscrit et annule son inscription auprès de Visual Studio.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        #region Register and unregister.
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");
        private static string languageName = "MyC";
        private static string eeName = "MyC Expression Evaluator";

        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");

        /// <summary>
        /// Register the expression evaluator.
        /// Set "project properties/configuration properties/build/register for COM interop" to true.
        /// </summary>
         [ComRegisterFunctionAttribute]
        public static void RegisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator";

            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);
            if (rk == null)  return;

            rk = rk.CreateSubKey(guidMycLang.ToString("B"));
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));
            rk.SetValue("CLSID", t.GUID.ToString("B"));
            rk.SetValue("Language", languageName);
            rk.SetValue("Name", eeName);

            rk = rk.CreateSubKey("Engine");
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));
        }
        /// <summary>
        /// Unregister the expression evaluator.
        /// </summary>
         [ComUnregisterFunctionAttribute]
        public static void UnregisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator\"
                        + guidMycLang.ToString("B");
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);
            if (key != null)
            {
                key.Close();
                Registry.LocalMachine.DeleteSubKeyTree(s);
            }
        }
    }
}
```

## <a name="unmanaged-code-expression-evaluator"></a>Évaluateur d’expression de code non managé
 La DLL EE implémente la `DllRegisterServer` fonction pour s’inscrire auprès de l’environnement com et de Visual Studio.

> [!NOTE]
> Vous pouvez trouver l’exemple de code du code MyCEE dans le fichier *dllentry. cpp*, qui se trouve dans l’installation VSIP sous EnVSDK\MyCPkgs\MyCEE.

### <a name="dll-server-process"></a>Processus serveur DLL
 Lors de l’inscription du EE, le serveur DLL :

1. Inscrit sa fabrique de classes `CLSID` conformément aux conventions com normales.

2. Appelle la fonction d’assistance `SetEEMetric` pour s’inscrire auprès de Visual Studio avec les métriques EE indiquées dans le tableau suivant. La fonction `SetEEMetric` et les métriques spécifiées comme suit font partie de la bibliothèque *dbgmetric. lib* . Pour plus d’informations, consultez [l’aide du kit de développement logiciel (SDK) pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) .

    |Métrique|Description|
    |------------|-----------------|
    |`metricCLSID`|`CLSID` de la fabrique de classes EE|
    |`metricName`|Nom du EE sous forme de chaîne affichable|
    |`metricLanguage`|Nom de la langue pour laquelle EE est conçu|
    |`metricEngine`|`GUID`s des moteurs de débogage (DE) qui fonctionnent avec ce EE|

    > [!NOTE]
    > `metricLanguage``GUID`Identifie le langage par son nom, mais il s’agit `guidLang` de l’argument de `SetEEMetric` qui sélectionne la langue. Lorsque le compilateur génère le fichier d’informations de débogage, il doit écrire le approprié `guidLang` afin que le de sache quel EE utiliser. Le DE demande généralement le fournisseur de symboles pour ce langage `GUID` , qui est stocké dans le fichier d’informations de débogage.

3. S’inscrit auprès de Visual Studio en créant des clés sous HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *x. y*, où *x. y* est la version de Visual Studio à inscrire.

### <a name="example"></a> Exemple
 La fonction suivante montre comment un code non managé (C++) EE s’inscrit et se désinscrit lui-même avec Visual Studio.

```cpp
/*---------------------------------------------------------
  Registration
-----------------------------------------------------------*/
#ifndef LREGKEY_VISUALSTUDIOROOT
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"
#endif

static HRESULT RegisterMetric( bool registerIt )
{
    // check where we should register
    const ULONG cchBuffer = _MAX_PATH;
    WCHAR wszRegistrationRoot[cchBuffer];
    DWORD cchFreeBuffer = cchBuffer - 1;
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);
    wcscat(wszRegistrationRoot, L"\\");

    // this is Environment SDK specific
    // we check for  EnvSdk_RegKey environment variable to
    // determine where to register
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;
    DWORD cchEnvVarRead = GetEnvironmentVariableW(
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value
        /* DWORD   */ cchFreeBuffer);// size of buffer
    if (cchEnvVarRead >= cchFreeBuffer)
        return E_UNEXPECTED;
    // If the environment variable does not exist then we must use
    // LREGKEY_VISUALSTUDIOROOT which has the version number.
    if (0 == cchEnvVarRead)
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);

    if (registerIt)
    {
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricCLSID,
                    CLSID_MycEE,
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricName,
                    GetString(IDS_INFO_MYCDESCRIPTION),
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricLanguage, L"MyC",
                    wszRegistrationRoot);

        GUID engineGuids[2];
        engineGuids[0] = guidCOMPlusOnlyEng;
        engineGuids[1] = guidCOMPlusNativeEng;
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricEngine,
                    engineGuids,
                    2,
                    wszRegistrationRoot);
    }
    else
    {
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricCLSID,
                        wszRegistrationRoot);
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricName,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricLanguage,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricEngine,
                        wszRegistrationRoot );
    }

    return S_OK;
}
```

## <a name="see-also"></a>Voir aussi
- [Écriture d’un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Applications auxiliaires du kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
