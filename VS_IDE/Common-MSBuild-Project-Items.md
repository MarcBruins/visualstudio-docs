---
title: "Common MSBuild Project Items"
ms.custom: na
ms.date: 10/10/2016
ms.devlang: 
  - VB
  - CSharp
  - C++
  - jsharp
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - vs-ide-sdk
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: 17
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# Common MSBuild Project Items
In MSBuild, an item is a named reference to one or more files. Items contain metadata such as file names, paths, and version numbers. All project types in Visual Studio have several items in common. These items are defined in the file microsoft.build.commontypes.xsd.  
  
## Common Items  
 The following is a list of all the common project items.  
  
### Reference  
 Represents an assembly (managed) reference in the project.  
  
|Item Name|Description|  
|---------------|-----------------|  
|HintPath|Optional string. Relative or absolute path of the assembly.|  
|Name|Optional string. The display name of the assembly, for example, "System.Windows.Forms."|  
|FusionName|Optional string. Specifies the simple or strong fusion name for the item.<br /><br /> When this attribute is present, it can save time because the assembly file does not have to be opened to obtain the fusion name.|  
|SpecificVersion|Optional boolean. Specifies whether only the version in the fusion name should be referenced.|  
|Aliases|Optional string. Any aliases for the reference.|  
|Private|Optional boolean. Specifies whether the reference should be copied to the output folder. This attribute matches the **Copy Local** property of the reference that's in the Visual Studio IDE.|  
  
### COMReference  
 Represents a COM (unmanaged) component reference in the project.  
  
|Item Name|Description|  
|---------------|-----------------|  
|Name|Optional string. The display name of the component.|  
|Guid|Optional string. A GUID for the component, in the form {12345678-1234-1234-1234-1234567891234}.|  
|VersionMajor|Optional string. The major part of the version number of the component. For example, "5" if the full version number is "5.46."|  
|VersionMinor|Optional string. The minor part of the version number of the component. For example, "46" if the full version number is "5.46."|  
|LCID|Optional string. The LocaleID for the component.|  
|WrapperTool|Optional string. The name of the wrapper tool that is used on the component, for example, "tlbimp."|  
|Isolated|Optional boolean. Specifies whether the component is a reg-free component.|  
  
### COMFileReference  
 Represents a list of type libraries that feed into the ResolvedComreference target.  
  
|Item Name|Description|  
|---------------|-----------------|  
|WrapperTool|Optional string. The name of the wrapper tool that is used on the component, for example, "tlbimp."|  
  
### NativeReference  
 Represents a native manifest file or a reference to such a file.  
  
|Item Name|Description|  
|---------------|-----------------|  
|Name|Required string. The base name of the manifest file.|  
|HintPath|Required string. The relative path of the manifest file.|  
  
### ProjectReference  
 Represents a reference to another project.  
  
|Item Name|Description|  
|---------------|-----------------|  
|Name|Optional string. The display name of the reference.|  
|Project|Optional string. A GUID for the reference, in the form {12345678-1234-1234-1234-1234567891234}.|  
|Package|Optional string. The path of the project file that is being referenced.|  
  
### Compile  
 Represents the source files for the compiler.  
  
|Item Name|Description|  
|---------------|-----------------|  
|DependentUpon|Optional string. Specifies the file this file depends on to compile correctly.|  
|AutoGen|Optional boolean. Indicates whether the file was generated for the project by the Visual Studio integrated development environment (IDE).|  
|Link|Optional string. The notational path to be displayed when the file is physically located outside the influence of the project file.|  
|Visible|Optional boolean. Indicates whether to display the file in **Solution Explorer** in Visual Studio.|  
|CopyToOutputDirectory|Optional string. Determines whether to copy the file to the output directory. Values are:<br /><br /> 1.  Never<br />2.  Always<br />3.  PreserveNewest|  
  
### EmbeddedResource  
 Represents resources to be embedded in the generated assembly.  
  
|Item Name|Description|  
|---------------|-----------------|  
|DependentUpon|Optional string. Specifies the file this file depends on to compile correctly|  
|Generator|Required string. The name of any file generator that is run on this item.|  
|LastGenOutput|Required string. The name of the file that was created by any file generator that ran on this item.|  
|CustomToolNamespace|Required string. The namespace in which any file generator that runs on this item should create code.|  
|Link|Optional string. The notational path is displayed if the file is physically located outside the influence of the project.|  
|Visible|Optional boolean. Indicates whether to display the file in **Solution Explorer** in Visual Studio.|  
|CopyToOutputDirectory|Optional string. Determines whether to copy the file to the output directory. Values are:<br /><br /> 1.  Never<br />2.  Always<br />3.  PreserveNewest|  
|LogicalName|Required string. The logical name of the embedded resource.|  
  
### Content  
 Represents files that are not compiled into the project, but may be embedded or published together with it.  
  
|Item Name|Description|  
|---------------|-----------------|  
|DependentUpon|Optional string. Specifies the file this file depends on to compile correctly.|  
|Generator|Required string. The name of any file generator that runs on this item.|  
|LastGenOutput|Required string. The name of the file that was created by any file generator that was run on this item.|  
|CustomToolNamespace|Required string. The namespace in which any file generator that runs on this item should create code.|  
|Link|Optional boolean. Indicates whether to display the file in **Solution Explorer** in Visual Studio.|  
|PublishState|Required string. The publish state of the content, either:<br /><br /> -   Default<br />-   Included<br />-   Excluded<br />-   DataFile<br />-   Prerequisite|  
|IsAssembly|Optional boolean. Specifies whether the file is an assembly.|  
|Visible|Optional boolean. Indicates whether to display the file in **Solution Explorer** in Visual Studio.|  
|CopyToOutputDirectory|Optional string. Determines whether to copy the file to the output directory. Values are:<br /><br /> 1.  Never<br />2.  Always<br />3.  PreserveNewest|  
  
### None  
 Represents files that should have no role in the build process.  
  
|Item Name|Description|  
|---------------|-----------------|  
|DependentUpon|Optional string. Specifies the file this file depends on to compile correctly.|  
|Generator|Required string. The name of any file generator that is run on this item.|  
|LastGenOutput|Required string. The name of the file that was created by any file generator that ran on this item.|  
|CustomToolNamespace|Required string. The namespace in which any file generator that runs on this item should create code.|  
|Link|Optional string. The notational path to be displayed if the file is physically located outside the influence of the project.|  
|Visible|Optional boolean. Indicates whether to display the file in **Solution Explorer** in Visual Studio.|  
|CopyToOutputDirectory|Optional string. Determines whether to copy the file to the output directory. Values are:<br /><br /> 1.  Never<br />2.  Always<br />3.  PreserveNewest|  
  
### BaseApplicationManifest  
 Represents the base application manifest for the build, and contains ClickOnce deployment security information.  
  
### CodeAnalysisImport  
 Represents the FxCop project to import.  
  
### Import  
 Represents assemblies whose namespaces should be imported by the Visual Basic compiler.  
  
## See Also  
 [Common MSBuild Project Properties](../VS_IDE/Common-MSBuild-Project-Properties.md)