---
title: L’inscription d’un évaluateur d’Expression | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2031657091a2209d4e358998159581d2159a5443
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251203"
---
# <a name="register-an-expression-evaluator"></a>Inscrire un évaluateur d’expression
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L’évaluateur d’expression (EE) doit s’inscrire en tant qu’une fabrique de classe avec l’environnement Windows COM et le Visual Studio. Un EE est configuré en tant que DLL afin qu’elle est injectée dans l’espace d’adressage de débogage moteur (dé) ou l’espace d’adressage de Visual Studio, selon lequel entité instancie le EE.  
  
## <a name="managed-code-expression-evaluator"></a>Évaluateur d’expression de code managé  
 Un code managé EE est implémenté comme une bibliothèque de classes, qui est une DLL qui s’inscrit auprès de l’environnement COM, généralement démarrée par un appel au programme VSIP, *regpkg.exe*. Le processus réel de l’écriture de clés de Registre pour l’environnement COM est géré automatiquement.  
  
 Une méthode de la classe principale est marquée avec <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, indiquant que la méthode à appeler lorsque la DLL est en cours d’inscription auprès de COM. Cette méthode d’inscription, souvent appelée `RegisterClass`, effectue la tâche d’inscription de la DLL avec Visual Studio. Correspondante `UnregisterClass` (marquée avec le <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), annule les effets de `RegisterClass` lorsque la DLL est désinstallée.  
 Les mêmes entrées de Registre sont effectuées que pour un EE écrit en code non managé ; la seule différence est que ne pose aucune fonction d’assistance telles que `SetEEMetric` pour effectuer le travail pour vous. Voici un exemple du processus d’inscription et d’annulation.  
  
### <a name="example"></a>Exemple  
 La fonction suivante montre comment un code managé EE inscrit et annule l’inscription d’elle-même avec Visual Studio.  
  
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
 La DLL EE implémente le `DllRegisterServer` fonction s’enregistrer auprès de l’environnement COM, ainsi que Visual Studio.  
  
> [!NOTE]
>  Yoou trouverez le code de Registre d’exemple de code MyCEE dans le fichier *dllentry.cpp*, qui se trouve dans l’installation de VSIP sous EnVSDK\MyCPkgs\MyCEE.  
  
### <a name="dll-server-process"></a>Processus de serveur DLL  
 Lorsque vous inscrivez le EE, le serveur de la DLL :  
  
1.  Inscrit la fabrique de classe `CLSID` conformément aux conventions de COM normales.  
  
2.  Appelle la fonction d’assistance `SetEEMetric` à inscrire avec Visual Studio, les mesures EE indiqués dans le tableau suivant. La fonction `SetEEMetric` et les mesures spécifiées comme suit font partie de la *dbgmetric.lib* bibliothèque. Consultez [aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) pour plus d’informations.  
  
    |Métrique|Description|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` de la fabrique de classe EE|  
    |`metricName`|Nom de la EE sous forme de chaîne affichable|  
    |`metricLanguage`|Le nom de la langue la EE est conçu pour évaluer|  
    |`metricEngine`|`GUID`s des moteurs de débogage (dé) qui fonctionnent avec cette EE|  
  
    > [!NOTE]
    >  Le `metricLanguage``GUID` identifie la langue par nom, mais il est le `guidLang` argument `SetEEMetric` qui sélectionne la langue. Lorsque le compilateur génère le fichier d’informations de débogage, il doit écrire approprié `guidLang` afin que l’Allemagne sache quel EE à utiliser. Le DE demande généralement le fournisseur de symboles pour ce langage `GUID`, qui est stocké dans le fichier d’informations de débogage.  
  
3.  Inscrit avec Visual Studio en créant des clés sous HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, où *X.Y* est la version de Visual Studio pour inscrire auprès de.  
  
### <a name="example"></a>Exemple  
 La fonction suivante montre comment un code non managé (C++) EE inscrit et annule l’inscription d’elle-même avec Visual Studio.  
  
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
 [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
