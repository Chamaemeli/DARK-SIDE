program Project1;

{$R *.res}

uses Messages, Windows;

 const AppName='Project1';
 procedure Delay(ms : longint);
             {$IFNDEF WIN32}
             var
               TheTime : LongInt;
             {$ENDIF}
             begin
             {$IFDEF WIN32}
               Sleep(ms);
             {$ELSE}
               TheTime := GetTickCount + ms;
               while GetTickCount < TheTime do
                 Application.ProcessMessages;
             {$ENDIF}
             end;
 Var


     Wnd:HWnd;
     Msg:TMsg;
     WindowsClass:TWndClass;
     hDC:integer;
     PAINTSTRUCT:TPaintStruct;
     hbr:HBRUSH;

function WindowProc (Window : HWnd ; Message : Word; WParam , LParam : LongInt ) : LongInt;
stdcall ;
begin
  WindowProc := 0 ;
  case Message of

  WM_Destroy :
  begin
    PostQuitMessage (0);
    Exit;
  end;

  WM_LBUTTONDOWN :
  begin
     Beep(392,350);
     Beep(392,350);
     Beep(392,350);
     Beep(311,250);
     Beep(466,100);
     Beep(392,350);
     Beep(311,250);
     Beep(466,100);
     Beep(392,700);
     Beep(587,350);
     Beep(587,350);
     Beep(587,350);
     Beep(622,250);
     Beep(466,100);
     Beep(369,350);
     Beep(311,250);
     Beep(466,100);
     Beep(392,700);
     Beep(784,350);
     Beep(392,250);
     Beep(392,100);
     Beep(784,350);
     Beep(739,250);
     Beep(698,100);
     Beep(659,100);
     Beep(622,100);
     Beep(659,200);
     Delay(300);
     Beep(415,100);
     Beep(554,350);
     Beep(523,250);
     Beep(493,100);
     Beep(466,100);
     Beep(440,100);
     Beep(466,200);
     Delay(300);
     Beep(311,100);
     Beep(369,350);
     Beep(311,250);
     Beep(466,100);
     Beep(392,350);
     Beep(311,250);
     Beep(466,100);
     Beep(392,750);
  end;

  WM_Paint :
  begin
    hDC := BeginPaint (Window , PAINTSTRUCT );
    FillRect ( hDC , PAINTSTRUCT.rcPaint, hbr);
    DrawText ( hDC , PChar ('Roma WinApi (Choose a dark side)') , -1 , PAINTSTRUCT.rcPaint , DT_SINGLELINE or DT_CENTER or DT_VCENTER );
    EndPaint (Window , PAINTSTRUCT );
  end;
  end;
  WindowProc := DefWindowProc (Window , Message , WParam , LParam ) ;


end;

begin
  with WindowsClass do
  begin
    Style := cs_HRedraw or cs_Vredraw ;
    lpfnWndProc := @ WindowProc ;
    cbClsExtra := 0 ;
    cbWndExtra := 0 ;
    hInstance := 0 ;
    hIcon := LoadIcon ( 0 , idi_Application ) ;
    hCursor := LoadCursor ( 0 , idc_Arrow ) ;
    hbrBackground := GetStockObject ( WHITE_BRUSH ) ;
    lpszMenuName := '' ;
    lpszClassName := AppName ;
  end;

  if RegisterClass ( WindowsClass ) = 0 then Halt ;
  Wnd := CreateWindow ( AppName , 'Project1' , ws_OverlappedWindow ,
  cw_UseDefault , cw_UseDefault , cw_UseDefault ,
  cw_UseDefault , 0 , 0 , HInstance , nil ) ;
  ShowWindow ( Wnd , SW_SHOW ) ;
  UpdateWindow ( Wnd ) ;

  while GetMessage ( Msg , 0 , 0 , 0 ) do
  begin
    TranslateMessage ( Msg );
    DispatchMessage ( Msg );
  end;
  Halt( Msg.wParam );
end.
