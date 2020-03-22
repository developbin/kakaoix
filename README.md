1. 기술 구성
 1-1. 백엔드
   - Spring boot, Gradle, Jpa
 1-2. 프론트 엔드
   - Vuejs(Vue-cli), bootstrapVue
 1-3. DB : mariadb

 1-4. 추가 설명 : 백엔드는 rest api 기반으로 구성을 하였고, 프론트엔드는 spa & csr 로 구성하였습니다.

2. 테이블 설계

 2-1. DDL
 
 2-2. todoMaster (마스터 테이블)
	CREATE TABLE `todomaster` (
		`todoId` INT(11) NOT NULL AUTO_INCREMENT,
		`name` VARCHAR(200) NOT NULL,
		`status` TINYINT(1) NULL DEFAULT 0,
		`addDt` DATETIME NOT NULL,
		`modifyDt` DATETIME NULL DEFAULT NULL,
		PRIMARY KEY (`todoId`)
	)
	COLLATE='utf8_general_ci'
	ENGINE=InnoDB
	AUTO_INCREMENT=56
	;
 2-3. todoDetail (디테일 테이블)
     CREATE TABLE `tododetail` (
	`todoId` INT(11) NOT NULL,
	`referTodoId` INT(11) NOT NULL,
	PRIMARY KEY (`todoId`, `referTodoId`),
	CONSTRAINT `FK_tododetail_todomaster` FOREIGN KEY (`todoId`) REFERENCES `todomaster` (`todoId`)
	)
	COLLATE='utf8_general_ci'
	ENGINE=InnoDB
	;
	
3. 기능 설명
 - CRUD 기능 완료
 - 검색, 날짜, 완료여부 검색 필더 기능 완료
 - 엑셀 다운로드, 파일 업로드 기능 완료
 
4. 빌드 및 실행방법.
 4-1. 개발 환경
   - 스프링 부트 어플리케이션을 run 합니다.
   - 디렉토리 frontend 접근하여 처음 기동하시는 경우 npm install을 진행해주시기 바랍니다.
   - 디렉토리 frontend 접근하여 npm run dev 명령어를 치시면 개발계 localhost:8089 vue-cli 기동이 됩니다.
   - localhost:8089 접속을 해주시면 됩니다.
   
 4-2. production 환경
   - 디렉토리 frontend 접근하여 npm run build 명령어를 치시면 Spring boot resource/static/ path에 빌드가 됩니다.
   - 스프링 부트 어플리케이션을 run 합니다.
   - localhost:8080 접속을 해주시면 됩니다.
