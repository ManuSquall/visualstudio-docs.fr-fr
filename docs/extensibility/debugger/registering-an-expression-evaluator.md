---
title: Enregistrement d’un évaluateur d’expression (en anglais) Microsoft Docs
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
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713199"
---
# <a name="register-an-expression-evaluator"></a>Enregistrer un évaluateur d’expression
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’évaluateur d’expression (EE) doit s’inscrire comme une usine de classe avec l’environnement Windows COM et Visual Studio. Un EE est mis en place comme un DLL de sorte qu’il est injecté dans l’espace d’adresse du moteur de débogé (DE) ou l’espace d’adresse Visual Studio, selon l’entité instantanément l’EE.

## <a name="managed-code-expression-evaluator"></a>Évaluateur d’expression de code géré
 Un code géré EE est mis en œuvre comme une bibliothèque de classe, qui est un DLL qui s’inscrit avec l’environnement COM, généralement commencé par un appel au programme VSIP, *regpkg.exe*. Le processus réel d’écriture des clés de registre pour l’environnement COM est géré automatiquement.

 Une méthode de la classe <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>principale est marquée par , indiquant que la méthode doit être appelée lorsque le DLL est enregistré auprès de COM. Cette méthode d’enregistrement, souvent appelée, `RegisterClass`accomplit la tâche d’enregistrer le DLL avec Visual Studio. Un `UnregisterClass` correspondant (marqué <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>avec le ), `RegisterClass` annule les effets de quand le DLL est désinstallé.
Les mêmes inscriptions au registre sont faites comme pour une EE écrite en code non menté; la seule différence est qu’il n’y a pas de fonction d’aide telle que `SetEEMetric` de faire le travail pour vous. Voici un exemple du processus d’enregistrement et de non-enregistrement.

### <a name="example"></a>Exemple
 La fonction suivante montre comment un code géré EE s’enregistre et se désinscrit avec Visual Studio.

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

## <a name="unmanaged-code-expression-evaluator"></a>Évaluateur d’expression de code non gestion
 L’EE DLL `DllRegisterServer` met en œuvre la fonction de s’inscrire à l’environnement COM ainsi qu’à Visual Studio.

> [!NOTE]
> Vous pouvez trouver le code MyCEE code d’enregistrement d’échantillon dans le fichier *dllentry.cpp*, qui est situé dans l’installation VSIP sous EnVSDK-MyCPkgs-MyCEE.

### <a name="dll-server-process"></a>Processus serveur DLL
 Lors de l’enregistrement de l’EE, le serveur DLL :

1. Enregistre son usine `CLSID` de classe selon les conventions normales de COM.

2. Appelle la fonction `SetEEMetric` d’aide pour s’inscrire auprès de Visual Studio les mesures EE indiquées dans le tableau suivant. La `SetEEMetric` fonction et les mesures spécifiées comme suit font partie de la bibliothèque *dbgmetric.lib.* Voir [les aides SDK pour débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) pour plus de détails.

    |Métrique|Description|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`de l’usine de classe EE|
    |`metricName`|Nom de l’EE comme une chaîne displayable|
    |`metricLanguage`|Le nom de la langue que l’EE est conçu pour évaluer|
    |`metricEngine`|`GUID`s des moteurs de débogé (DE) qui fonctionnent avec cette EE|

    > [!NOTE]
    > Le `metricLanguage``GUID` identifie la langue par le `guidLang` nom, `SetEEMetric` mais c’est l’argument à qui sélectionne la langue. Lorsque le compilateur génère le fichier d’information de `guidLang` débogé, il doit écrire le approprié afin que le DE sache quel EE utiliser. Le DE demande généralement au `GUID`fournisseur de symboles pour cette langue, qui est stockée dans le fichier d’information de déboçon.

3. S’inscrit auprès de Visual Studio en créant des clés sous\\HKEY_LOCAL_MACHINE-MICROSOFT-VisualStudio*X.Y*, où *X.Y* est la version de Visual Studio avec qui s’inscrire.

### <a name="example"></a>Exemple
 La fonction suivante montre comment un code non managérional (C) EE s’enregistre et s’enregistre avec Visual Studio.

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
- [Rédaction d’un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
