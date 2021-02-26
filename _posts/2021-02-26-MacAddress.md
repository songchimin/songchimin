---
layout: post
title: "로컬 Mac Address"
categories:
  - Markup
tags:
  - MacAddress
  - Java
---

## 로컬 Mac Address 확인

```java

import java.util.ArrayList;

import org.jnetpcap.Pcap;
import org.jnetpcap.PcapIf;

public class Main {

	public static void main(String[] args) {
		
		ArrayList<PcapIf> allDevs = new ArrayList<PcapIf>(); 
		// 디바이스를 담을 변수를 ArrayList로 생성
		StringBuilder errbuf = new StringBuilder();	
		// 에러처리
		
		int r = Pcap.findAllDevs(allDevs, errbuf);	
		// 접근가능한 디바이스를 첫번째인자에담는다, 2번째인자는에러처리
		
		if (r==Pcap.NOT_OK || allDevs.isEmpty()) {
			System.out.println("네트워크 장치 찾기 실패." + errbuf.toString());
			return;
		}	// 예외처리
		
		System.out.println("< 탐색된 네트워크 Device >");
		
		try {
			for (final PcapIf i : allDevs) {
				// 탐색된 네트워크 디바이스를 하나씩 출력
				final byte[] mac = i.getHardwareAddress();
				// Mac Address를 얻어온다.
				if (mac == null) {
					continue;	// Mac Address가 없는경우 건너뛴다.
				}
				System.out.printf("장치 주소: %s\nMac Address: %s\n", i.getName(), asString(mac));
				// asString을 이용하여 바이트형태의 맥을 문자열로 출력
			}
		} catch (Exception e){
			e.printStackTrace();
		}
	}
	
	private static String asString(final byte[] mac) 
	{	// 6Byte 형태의 Mac을 문자열로 변경하는 함수
		final StringBuilder buf = new StringBuilder();
		for (byte b : mac) {
			if(buf.length() != 0) {	// 첫번째 제외하고 :를붙인다
				buf.append(":");
			}
			if(b >= 0 && b < 16) { //16미만일시 한 자릿수 출력
				buf.append('0');
			}
			buf.append(Integer.toHexString((b < 0) ? b + 256 : b).toUpperCase());
			// 16 이상이면 두 자릿수 그대로 출력
		}
		return buf.toString();
	}
}

```