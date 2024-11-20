# MariOver
The backend of [the Mario Maker 2 API](https://tgrcode.com/mm2/docs/). Hey Nintendo, it's MariOver.

# Setting up
0. Run `pip install -r requirements.txt`
1. Obtain `PRODINFO`, Mario Maker 2 base ticket with console specific data included, and `prod.keys`.
    1. Run `Lockpick_RCM` and download `prod.keys`, which is in `/switch` on your SD card, onto your PC
    2. `PRODINFO` can be obtained using `Memloader`, contained within `Tegra RCM GUI`, combined with `NxNandManager`
    3. Start `Memloader` with `rawNAND` and run `NxNandManager`. Press `Options->Configure keyset` and import your `prod.keys`
    4. Choose the `linux` device in `File->Open drive` and right click `PRODINFO` and click `Decrypt and dump to file`
    5. Close `NxNandManager` and hold the power button on your switch to shut it off
    6. Download `nxdumptool` to your switch and dump the base ticket, downloading it to your PC
    7. Put `PRODINFO.dec`, the base ticket and `prod.keys` into a new folder in this repository named `ConsoleData`
2. Download `TegraExplorer` to your switch and boot into it
    1. Browse EMMC and navigate to `SYSTEM/save/8000000000000010`, copying it to your clipboard. Navigate back to the `sd` card and paste it there
    2. Download that file from your switch and place it in `ConsoleData`
3. Run `python generate_console_data.py`
4. When you update your switch and `NintendoClients` has updated, run `pip install git+https://github.com/kinnay/NintendoClients.git --upgrade` and run `python generate_console_data.py` again

# Running
`uvicorn levelInfoWebserver:app --port 1234` with any port can be used to start the server. Documentation can be found at `http://localhost:1234/docs/`.

# MariOver

Mario Maker 2 API의 백엔드입니다. 안녕 닌텐도, 이것은 MariOver입니다.

## 설정하기

0. pip install -r requirements.txt를 실행합니다.
1. 콘솔 특정 데이터가 포함된 PRODINFO, Mario Maker 2 베이스 티켓, 그리고 prod.keys를 얻습니다.

   1. Lockpick_RCM을 실행하고, SD 카드의 /switch에 있는 prod.keys를 PC로 다운로드합니다. 
   2. PRODINFO는 Tegra RCM GUI에 포함된 Memloader와 NxNandManager를 사용하여 얻을 수 있습니다. 
   3. Memloader를 rawNAND로 시작하고 NxNandManager를 실행합니다. Options->Configure keyset을 눌러 prod.keys를 가져옵니다. 
   4. File->Open drive에서 linux 장치를 선택하고 `PRODINFO`를 오른쪽 클릭하여 Decrypt and dump to file을 클릭합니다. 
   5. `NxNandManager`를 닫고 스위치의 전원 버튼을 길게 눌러 전원을 끕니다. 
   6. 스위치에 `nxdumptool`을 다운로드하고 베이스 티켓을 덤프하여 PC로 다운로드합니다. 
   7. 이 리포지토리의 `ConsoleData`라는 새 폴더에 `PRODINFO.dec`, 베이스 티켓, 그리고 `prod.keys`를 넣습니다.

2. 스위치에 `TegraExplorer`를 다운로드하고 부팅합니다.

   1. EMMC를 탐색하고 `SYSTEM/save/8000000000000010`으로 이동하여 이를 클립보드에 복사합니다. sd 카드로 돌아가서 거기에 붙여넣습니다. 
   2. 해당 파일을 스위치에서 다운로드하여 `ConsoleData`에 넣습니다. 
   3. `python generate_console_data.py`를 실행합니다. 
   4. 스위치와 NintendoClients를 업데이트할 때, `pip install git+https://github.com/kinnay/NintendoClients.git --upgrade`를 실행하고 `python generate_console_data.py`를 다시 실행합니다.

## 실행하기

임의의 포트로 uvicorn levelInfoWebserver:app --port 1234를 사용하여 서버를 시작할 수 있습니다.<br />
문서는 http://localhost:1234/docs/ 에서 찾을 수 있습니다.