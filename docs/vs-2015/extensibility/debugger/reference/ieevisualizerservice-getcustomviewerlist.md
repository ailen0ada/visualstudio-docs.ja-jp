---
title: IEEVisualizerService::GetCustomViewerList |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e037ac728c47b2b4610d866b2ba3868dc44b4eb0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533244"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IEEVisualizerService::GetCustomViewerList](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist)します。  
  
このメソッドは、このサービスが知っている型のビジュアライザーのリストを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celtSkip`  
 [in]ビジュアライザーをスキップの数。  
  
 `celRequested`  
 [in]取得するビジュアライザーの数 (ものサイズを指定します、`rgViewers`配列)。  
  
 `rgViewers`  
 [入力、出力]配列[DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)情報を格納する構造体。  
  
 `pceltFetched`  
 [out]ビジュアライザーの数を実際に取得します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)型のビジュアライザーのサポートの一部として要求をこのメソッドに渡します。 入力を適切を追加できる場合は、式エバリュエーターでは、同じ型のカスタム ビューアーも用意されて、 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)リストにこれらのカスタム ビューアーの構造体。 必ず[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)その他のビューアーが反映されます。  
  
 参照してください[型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)ビジュアライザーとビューアーとの違いの詳細について。  
  
## <a name="see-also"></a>関連項目  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

