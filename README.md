# java_06_array
package ch07_array;

import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;
import java.text.BreakIterator;
import java.util.Scanner;

/**
 * Class Name : OperatorMain2024. 1. 3. Author : Kimgichan Created Date: 2024.
 * 1. 3. Version : 1.0 Purpose : operator study Descitption : if 와 조건문
 */
public class ArrayMain {

	public static void main(String[] args) throws NoSuchAlgorithmException {
		String samjang = "삼장";
		String ogong = "오공";
		String saojeong = "사오정";
		String palgye = "저팔계";
		// 배열(array)
		// String[] 문자열 배열
		String[] seoyugi = new String[4];// 첨자는 배열의 크기(단순 array 크기변경x)
		System.out.println(seoyugi.length);// 배열의 길이를 리턴
		System.out.println(seoyugi[0]);// 처음 생성된 배여렝는 기본값(default)가 있음
		// 참조타임(String, Object..) : nu11
		// 기본타입(int, boolean..) : 숫자이면 0, boolean 이면 fales
		int[] numbers = new int[3];
		System.out.println(numbers[0]);
		boolean[] bools = new boolean[5];
		System.out.println(bools[0]);

		seoyugi[0] = samjang;
		seoyugi[1] = ogong;
		seoyugi[2] = saojeong;
		seoyugi[3] = palgye;
		System.out.println(seoyugi); // 주소출력
		printArr(seoyugi);
		for (int i = 0; i < seoyugi.length; i++) {
			// 배열의 첫 요소에서 부터 순회하며 변경
			seoyugi[i] = "서유기" + seoyugi[i];
		}
		printArr(seoyugi);
		// 오공이 포함되어있는 배열의 요소를 찾아서 서유기 ->드래곤볼 로 변경
		for (int i = 0; i < seoyugi.length; i++) {
			// '대상문자열'. contains("찾을문자열")<---- 포함되어있으면 turn
			if (seoyugi[i].contains("오공")) {
				seoyugi[i] = seoyugi[i].replace("서유기", "드래곤본");
			}
		}
		printArr(seoyugi);
		// 값을 넣으면 배열 선언
		String[] students = { "팽수", "길동", "동길", "길수" };
//	    String[] students =new String[] {"팽수","길동","동길","길수"}; //위와 동일함.
		printArr(students);
		String subject = "JAVA,DB,JSP,HTML";
		// 대상문자열.split(구분자)<--- 구분자로 문자열을 나누어 배열로 리턴
		String[] subArr = subject.split(",");
		printArr(subArr);
		// // 문자열 양쪽 공백제거
		for (int i = 0; i < subArr.length; i++) {
			subArr[i] = subArr[i].trim(); // trim <--양쪽공백제거
		}
		printArr(subArr);

		// 배열의 복사 1.얇은 복사? Shallow copy 주소값 복사
		String[] sinSeoyugi = seoyugi; // 주소가 복사된거임.
		printArr(sinSeoyugi);
		sinSeoyugi[0] = "강호동";// 동일 주소이기 때문에 값 변경시 두 변수 다 변경되어 보임.
		printArr(seoyugi);
		printArr(sinSeoyugi);

		// 깊은 복사(deep copy) 새로운 객체 (주소가 다름)
		String[] newSeoyugi = seoyugi.clone();
		newSeoyugi[2] = "은지원";
		printArr(sinSeoyugi);
		printArr(newSeoyugi);

		// clone 까먹었다!?
		String[] copy = new String[seoyugi.length];
		for (int i = 0; i < seoyugi.length; i++) {
			copy[i] = seoyugi[i];
		}
		// @앞은 객체의 타입
		// @뒤에 붙은건 hashCode를 16진수로 나타낸것
		System.out.println(seoyugi);
		System.out.println(seoyugi.hashCode());
		// 숫자를 16진수로 변환
		System.out.println(Integer.toHexString(seoyugi.hashCode()));

		// 해쉬(hash) 란 ? 임의의 길이를 가진 데이터를 고정된 길이를 가진 데이터로 매핑한 것.
		// 이 과정에서 원본 데이터를(key), 매핑하는 과정을 해싱(hashing)
		// 결과물로 나온 데이터를 해쉬값 (Hash value)
		// 이렇게 데이터를 해싱하는 함수를 해시 함수(Hash function)이라고 함.
		String pw = "1234";
		String encode = encrypt(pw);
		System.out.println(encode);
		Scanner scan = new Scanner(System.in);
		while(true) {
			System.out.println("암호를 입력하시오!!");
			System.out.print(">>>");
			String msg = scan.nextLine();
			String userPw = encrypt(msg);
			if (userPw.equals(encode)) {
				System.out.println("로그인 되셨습니다.");
				break;
			} else {
				System.out.println("비번이 틀렸습니다.");
			}
		}
		
		
		//일차원 배열
		int[] oneD = {1,2,3}; 
		System.out.println(oneD[1]); //2
		//다차원 배열
		int[][] twoD= {{1,2,3},{4,5,6},{7,8,9}};
		//만약 2라는 값에 접근하려면?!
		System.out.println(twoD[0][1]);
		int[][][] threeD = {{{1,2,3},{4,5,6},{7,8,9}},{{10,11,12},{13,14,}}};
		System.out.println(threeD[0][0][1]);
		//만약 13을 출력하려면?
		System.out.println(threeD[1][1][0]);
		
		for(int i=0; i< twoD.length; i++) {
			
			for(int j=0; j<twoD[i].length; j++) {
//				printArr(twoD[]);
				System.out.println(twoD[i][j]);
			     /*
		 	      *    00,01,02
			      *    10,11,12
			      *    20,21,22
		          **/	
			
			
			
			
			
			
			
			}
		}
		
		
		
		
		
		
	}

	

	public static void printArr(String[] strArr) {
		for (int i = 0; i < strArr.length; i++) {
			if (i == strArr.length - 1) {
				System.out.println(strArr[i]);
				break;
			}
			System.out.print(strArr[i] + ",");
		}

	}

	// 해쉬 암호화
	public static String encrypt(String text) throws NoSuchAlgorithmException {
		MessageDigest md = MessageDigest.getInstance("SHA-256");
		md.update(text.getBytes());
		return byteToHex(md.digest());
	}

	private static String byteToHex(byte[] bytes) {
		StringBuilder builder = new StringBuilder();
		for (byte b : bytes) {
			builder.append(String.format("%02x", b));
		}
		return builder.toString();
	}
	public static void printArr(int[] strArr) {
		for (int i = 0; i < strArr.length; i++) {
			if (i == strArr.length - 1) {
				System.out.println(strArr[i]);
				break;
			}
			System.out.print(strArr[i] + ",");
		}

	}

}
