---
title: "Proc&#233;dure&#160;: exportation de param&#232;tres &#224; l’aide des assemblys d’interop&#233;rabilit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Paramètres IDE, exportation à l’aide des assemblys d’interopérabilité"
  - "paramètres utilisateur [SDK Visual Studio], exportation à l’aide des assemblys d’interopérabilité"
  - "IDE, exportation des paramètres à l’aide des assemblys d’interopérabilité"
ms.assetid: d470d4f9-3006-40c3-99db-21abcd5003b8
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# Proc&#233;dure&#160;: exportation de param&#232;tres &#224; l’aide des assemblys d’interop&#233;rabilit&#233;
Un VSPackage peut exporter des paramètres à partir de l’environnement de développement intégré \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. L’IDE utilise l’implémentation d’un VSPackage de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>. Si le package fournit également l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>, l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> est utilisée pour déterminer comment la configuration du VSPackage doit être enregistrée.  
  
> [!NOTE]
>  Managed Package Framework \(MPF\) fournit un ensemble de classes managées pour faciliter la création d’extensions Visual Studio. Pour effectuer cette tâche à l’aide de MPF, consultez [Exportation de paramètres](../misc/exporting-settings.md).  
  
### Pour implémenter l’exportation des paramètres dans un VSPackage  
  
1.  Implémentez la prise en charge de base du mécanisme de paramètres [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    -   Inscrivez le VSPackage comme prenant en charge le mécanisme de paramètres en définissant un ou plusieurs Points de paramètres personnalisés.  
  
         Pour plus d'informations, consultez [Prise en charge pour les paramètres utilisateur](../extensibility/internals/support-for-user-settings.md).  
  
    -   Déclarez que le VSPackage implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>. Si vous le souhaitez, le VSPackage peut également implémenter l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>. Exemple :  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   Vérifiez que l’implémentation de la méthode <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> du VSPackage fournit une interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> lorsqu’elle est appelée avec `IID_IVsUserSettings`.  
  
         Si vous le souhaitez, `QueryInterface` peut fournir une interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> lorsqu’elle est appelée avec l’interface `IID_IVsUserSettingsQuery`.  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  Si vous le souhaitez, informez l’IDE de la nécessité d’exporter un paramètre particulier.  
  
     Un VSPackage peut choisir d’enregistrer conditionnellement un paramètre défini par l’état du Point de paramètres personnalisés. Par exemple, vous pouvez effectuer un enregistrement uniquement si l’utilisateur indique explicitement un paramètre à enregistrer.  
  
     Dans ce cas, vous devez implémenter l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>.  
  
     Si un VSPackage n’implémente pas <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>, toutes ses informations d’état sont enregistrées lors d’une exportation de paramètres.  
  
     Un VSPackage peut prendre en charge plusieurs Points de paramètres personnalisés \(catégories de paramètres\). Les implémentations de la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery.NeedExport%2A> doivent vérifier le GUID du Point de paramètres personnalisés fourni ou l’argument de catégorie de paramètres pour déterminer si un groupe de paramètres particulier doit être enregistré.  
  
     Dans l’exemple ci\-dessous, le VSPackage demande toujours que l’état de sa barre de commandes soit enregistré, mais il demande que l’état des liaisons de clés soit enregistré seulement si un indicateur a été défini.  
  
3.  Écrivez les données de paramètres dans le fichier de paramètres.  
  
     Pour prendre en charge l’exportation des paramètres, un VSPackage doit toujours implémenter la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>.  
  
     L’implémentation doit gérer les arguments passés par l’IDE, le GUID de la catégorie de ce Point de paramètres personnalisés et une interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>.  
  
    1.  Un VSPackage peut prendre en charge plusieurs Points de paramètres personnalisés \(catégories de paramètres\). Dans l’exemple ci\-dessous, la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> appelle une implémentation différente pour rendre persistant l’état de la barre de commandes plutôt que l’état des liaisons de clés.  
  
    2.  Un VSPackage doit utiliser l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> fournie pour enregistrer les données dans le fichier de paramètres.  
  
         `interface IVsSettingsWriter : IUnknown`  
  
         `{`  
  
         `HRESULT WriteSettingString( LPCOLESTR pszSettingName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingLong( LPCOLESTR pszSettingName, long lSettingValue);`  
  
         `HRESULT WriteSettingBoolean( LPCOLESTR pszSettingName, BOOL fSettingValue);`  
  
         `HRESULT WriteSettingBytes( LPCOLESTR pszSettingName, BYTE *pSettingValue, long lDataLength);`  
  
         `HRESULT WriteSettingAttribute( LPCOLESTR pszSettingName, LPCOLESTR pszAttributeName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingXml( IUnknown *pIXMLDOMNode);`  
  
         `HRESULT WriteSettingXmlFromString( LPCOLESTR szXML);`  
  
         `HRESULT ReportError( LPCOLESTR pszError, VSSETTINGSERRORTYPES dwErrorType);`  
  
         `};`  
  
         La valeur de l’argument `pszSettingName` fourni à une interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> doit identifier de façon unique chaque élément de données enregistré dans une catégorie de paramètres.  
  
        > [!NOTE]
        >  Les noms doivent être uniques au sein d’un Point de paramètres personnalisés, car l’IDE utilise son GUID et la valeur de `pszSettingName` pour identifier chaque paramètre enregistré. Si plusieurs méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> sont appelées avec la même valeur de `pszSettingName`, la valeur d’origine est remplacée dans le fichier de paramètres.  
  
         Le fichier de paramètres prend en charge l’accès aléatoire aux données. Ainsi, l’ordre des opérations de lecture et d’écriture de paramètres n’est pas important.  
  
         Ceci est illustré dans les implémentations de l’exportation et de l’importation de l’état de barre de commandes \(`ExportSettings_CommandBa`r et `ImportSettings_CommandBar`\) dans l’exemple ci\-dessous.  
  
         Si l’implémentation peut mapper les données dans l’un des quatre formats pris en charge, il n’existe aucune restriction sur la quantité ou le type de données qui peuvent être écrites.  
  
        > [!NOTE]
        >  En plus des données écrites explicitement et transparentes pour l’implémentation <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>, l’API des paramètres enregistre également les informations sur la version [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous pouvez comparer les paramètres enregistrés à la version de l’IDE qui les a générés pendant l’importation des paramètres.  
  
## Exemple  
 L’exemple suivant montre comment importer et exporter des données de paramètres.  
  
```  
// -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export. //    Delegate to the right shell object based on the category GUID. // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to treat import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning, these settings should immediately //             be applied to your personal settings store, //             whether in the registry or the file system. // This write-through cache methodology is essential to to work //             in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether import can be treated as an additive // operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: Before returning, these settings should immediately //             be applied to your personal settings //             store, whether in the registry or the file system. // This write-through cache methodology is essential to allow us //             to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## Voir aussi  
 [Prise en charge pour les paramètres utilisateur](../extensibility/internals/support-for-user-settings.md)   
 [Options et paramètres d'extension utilisateur](../extensibility/extending-user-settings-and-options.md)   
 [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Procédure : utilisation des assemblys PIA pour importer des paramètres](../misc/how-to-use-interop-assemblies-to-import-settings.md)