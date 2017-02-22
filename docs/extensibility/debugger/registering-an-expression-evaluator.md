---
title: "L’inscription d’un &#233;valuateur d’Expression | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluation de l’expression [Debugging SDK], le débogage"
  - "évaluateurs d’expression, l’inscription"
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# L’inscription d’un &#233;valuateur d’Expression
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L’évaluateur d’expression \(EE\) doit s’enregistrer comme une fabrique de classe avec l’environnement COM de Windows et Visual Studio. Un EE est implémenté en tant que DLL afin qu’il peut être injectée dans l’espace d’adressage debug engine \(DE\) ou l’espace d’adressage de Visual Studio, selon lequel entité instancie le EE.  
  
## Évaluateur d’Expression de Code managé  
 Un code managé EE est implémenté comme une bibliothèque de classes, qui est une DLL qui s’enregistre auprès de l’environnement COM, généralement démarrée par un appel au programme VSIP, **regpkg.exe**. Le processus réel de l’écriture des clés de Registre pour l’environnement COM est géré automatiquement.  
  
 Une méthode de la classe principale est marquée avec la <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, indiquant que cette méthode doit être appelée lorsque la DLL est en cours d’inscription avec COM. Cette méthode d’inscription, souvent appelée `RegisterClass`, effectue la tâche d’inscription de la DLL avec Visual Studio. Correspondante `UnregisterClass` \(marquée avec le <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>\), annule les effets de `RegisterClass` lorsque la DLL est désinstallée.  
  
 Les mêmes entrées de Registre sont effectuées pour un EE écrit en code non managé ; la seule différence est qu’il est sans fonction d’assistance comme `SetEEMetric` pour effectuer le travail pour vous. Un exemple de ce processus d’inscription\/désinscription ressemble à ceci :  
  
### Exemple  
 Cette fonction indique comment un code managé EE enregistre et désenregistre les lui\-même avec Visual Studio.  
  
```c#  
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
  
## Évaluateur d’Expression de Code non managé  
 La DLL EE implémente la `DllRegisterServer` fonction s’enregistrer auprès de l’environnement COM, ainsi que Visual Studio.  
  
> [!NOTE]
>  Vous trouverez le code de Registre MyCEE code exemple dans le fichier dllentry.cpp, qui se trouve dans l’installation de VSIP sous EnVSDK\\MyCPkgs\\MyCEE.  
  
### Processus de serveur DLL  
 Lors de l’inscription du EE, le serveur de la DLL :  
  
1.  Inscrit la fabrique de classe `CLSID` selon les conventions COM normales.  
  
2.  Appelle la fonction d’assistance `SetEEMetric` à inscrire avec Visual Studio, les mesures EE indiqués dans le tableau suivant. La fonction `SetEEMetric` et les mesures spécifiées ci\-dessous font partie de la bibliothèque dbgmetric.lib. Pour plus d'informations, consultez [« Helpers » du Kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
    |Métrique|Description|  
    |--------------|-----------------|  
    |`metricCLSID`|`CLSID` de la fabrique de classe EE|  
    |`metricName`|Nom de la EE sous forme de chaîne affichable|  
    |`metricLanguage`|Le nom de la langue que le EE est conçu pour évaluer|  
    |`metricEngine`|`GUID`les moteurs de débogage \(DE\) qui fonctionnent avec ce EE s|  
  
    > [!NOTE]
    >  Le `metricLanguage``GUID` identifie la langue par nom, mais il est le `guidLang` argument `SetEEMetric` qui sélectionne la langue. Lorsque le compilateur génère le fichier d’informations de débogage, il doit écrire approprié `guidLang` afin que le DE sache quel EE à utiliser. Le DE demande généralement au fournisseur de symbole pour ce langage `GUID`, qui est stocké dans le fichier d’informations de débogage.  
  
3.  Inscrit avec Visual Studio en créant des clés sous HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*X.Y*, où *X.Y* est la version de Visual Studio pour enregistrer avec.  
  
### Exemple  
 Cette fonction indique comment un code non managé \(C\+\+\) EE inscrit et annule sa avec Visual Studio.  
  
```cpp#  
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
  
## Voir aussi  
 [Écriture d'un évaluateur d'Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [« Helpers » du Kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)