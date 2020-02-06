---
layout: post
title: "안드로이드 AsyncTask Http통신"
categories:
  - Markup
tags:
  - java
  - android
---

## 안드로이드 스튜디오 AsyncTask Http통신.

### Source

```html
<!-- Oncreate -->
    NetworkTask networkTask = new NetworkTask(url, null);
    networkTask.execute();




public class NetworkTask extends AsyncTask<Void, Void, String> {

        private String url;
        private ContentValues values;

        public NetworkTask(String url, ContentValues values) {

            this.url = url;
            this.values = values;
        }

        @Override
        protected String doInBackground(Void... params) {

            String result; // 요청 결과를 저장할 변수.
            RequestHttpConnection requestHttpURLConnection = new RequestHttpConnection();
            result = requestHttpURLConnection.request(url, values); // 해당 URL로 부터 결과물을 얻어온다.

            return result;
        }

        @Override
        protected void onPostExecute(String json) {
            super.onPostExecute(json);

            try {
                if (json != null) {
                    JSONObject jsonObject = new JSONObject(json);
                    JSONArray ListArray = jsonObject.getJSONArray("AndroidChatList");

                    chat_room_singerItem[] singerItems = new chat_room_singerItem[ListArray.length()];

                    for (int i = 0; i < ListArray.length(); i++) {

                        JSONObject ListObject = ListArray.getJSONObject(i);

                        singerItems[i] =
                                new chat_room_singerItem(
                                        String.valueOf(ListObject.getInt("chat_room_num")),
                                        ListObject.getString("chat_room_image"),
                                        ListObject.getString("chat_room_title"),
                                        ListObject.getString("chat_room_participant_count"));

                        adapter.addItem(singerItems[i]);

                    }
                    chat_room_list.setAdapter(adapter);

                } 

            } catch (JSONException e) {

                e.printStackTrace();
            }

        }
    }
````